# Instructions

The environment is set up here on MAGEOHub to make this work effectively.

To do the self-supervised bit, the key parts are to:

1. run python preprocessing/prepare_training.py
    this creates a .pkl file of training data. I need to work out what format this training data is in.
    
2. Run the following commands to do the self-supervised learning on a number of different radii and configurations 

python train_app1_self_narr.py --radius=1 --odir=r1_w2vec
python train_app1_self_narr.py --radius=3 --odir=r3_w2vec
python train_app1_self_narr.py --radius=5 --odir=r5_w2vec
python train_app1_self_narr.py --radius=7 --odir=r7_w2vec
python train_app1_self_narr.py --radius=9 --odir=r9_w2vec
python train_app1_self_narr.py --radius=3 --odir=r3_nbrs --nbrs_av=3
python train_app1_self_narr.py --radius=9 --odir=r9_nbrs --nbrs_av=9
python train_app1_self_narr.py --radius=3 --odir=r3_local --local
python train_app1_self_narr.py --radius=9 --odir=r9_local --local

3. After this, the results are basically done, and we just look at notebooks/visualize_selfsupervised.ipynb

This gives us the results, and we don't really know what happens in here that is important. It runs the causal inference? It does something with epochs. Then it outputs some error scores for the different methods...

I would like to do an analysis of this for my work...perhaps with bounds on the causal estimates...see Jesson's competitor.

Then we are all finished. I need to do this for temperature, and see how important it is

# To do

Get reanalysis data in suitable shape to put it into the prepare_training script. I need to use codex for this, or chatgpt.

Then adapt the self supervised algorithm to include a temporal component. This will be harder than it seems, and will likely require some thought about which step to do first. Temporal or spatial? And how to make a dataloader to do this sensibly?

Then run it. This step should be ok since we use propensity scores. I will have to mess around with the dimensionality necessary for this.