# Applied Deep Learning - Visual Question Answering - Vision + Language Model

# about

This project showcases multi-input models. I developed a model that takes a question and an image as input, and returns a yes/no answer in response. 

![Model](https://github.com/tmatrixhy/adl-visual-q-a/blob/master/model.jpg)

# results

Overall I found that the simple model that I originally implemented was easily one of the
best ones I tested.


--------------------------------------------
ORIGINAL MODEL - Info
--------------------------------------------

When I built my original model, I had made the following decisions:

1. Output Dimension: 256
   I wanted my output dimension for the Embedding to be higher as to acieve 
   better representation so I chose 256 as a starting point.
2. Required Dense Layer Neurons: 64
3. Total Epochs: 10.
4. Total model parameters: 1,440,962.

This was a rather big network with 1.5 million parameters, Training acc of 80%
was achieved within 10 minutes.

--------------------------------------------
TEST AREA 1 - Info
--------------------------------------------

I wanted to reduce the model size a bit and see how well I could get a smaller
network to perform. I was able to achieve nearly the same accuracy while having
the following hyperparameters.

1. Output Dimension: 64
2. Required Dense Layer Neurons: 32
3. Additional Dense Layer Neurons: 16
4. Total Epochs: 20
5. Total model parameters: 293,202

With nearly a 5 fold model size decrease compared to the original model , the 
same training accuracy is achieved. However the trade off is time. It takes 2x
as long to achieve a similar accuracy. The model also has a strong plateau after
epoch 14.

--------------------------------------------
TEST AREA 2 - Info
--------------------------------------------
Shooting for a middle of the road model with as much accuracy as I can get with
20 epochs.

1. Output Dimension: 128
2. Required Dense Layer Neurons: 128
3. Two additional Dense layer Neurons: 64 / 32
4. Total Epocs: 20
5. Total model parameters: 804,642

Model achieves nearly same accuracy as original model in almost the same epochs 
using nearly half trainable parameters. Training plateaus after epoch 13.

--------------------------------------------
TEST AREA 3 - Info
--------------------------------------------
I wanted to see if I could optimize the network with the same amount of tranable
parameters as the original model but a different model setup.

1. Output Dimension: 256 
2. Total LSTM Layers: 3
3. Required Dense Layer Neurons: 32
4. Total Epocs: 5
5. Total model parameters: 1,607,522

Training time for 3 LSTM networks is roughly 24 seconds longer per epoch.
MODEL DOES NOT CONVERGE. STOPPED TRAINING AFTER 5 EPOCS OF NO MOVEMENT IN
ACCURACY

--------------------------------------------
TEST AREA 4 - Info
--------------------------------------------
Seeing if more than 1 LSTM layer is causing the degredation of the model.

1. Output Dimension: 128 
2. Total LSTM Layers: 2
3. Required Dense Layer Neurons: 64
4. Total Epocs: 5
5. Total model parameters: 632,674

MODEL DOES NOT CONVERGE. STOPPED TRAINING AFTER 5 EPOCS OF NO MOVEMENT IN
ACCURACY.

Cannot stack LSTM networks for VQA

--------------------------------------------
TEST AREA 5 - Info
--------------------------------------------
Seeing if more than 1 LSTM layer is causing the degredation of the model.

1. Output Dimension: 512 
2. Total LSTM Layers: 1
3. Required Dense Layer Neurons: 64+32
4. Total Epocs: 20
5. Total model parameters: 3,801,250

Model is much more accurate much faster.