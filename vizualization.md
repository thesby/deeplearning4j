---
title: 
layout: default
---

# Deeplearning4j's Vizualization and UI

        MultiLayerNetwork model = new MultiLayerNetwork(conf);
        model.init();
        model.setListeners(Arrays.asList((IterationListener) new     ScoreIterationListener(listenerFreq)));

The first line above calls build on the configuration. The second passes the configuration into an instance of a MultiLayerNetwork model. The third initializes the model. The fourth sets iteration listeners, which do all kinds of neat things. 

An *iterationListener* is a hook, a plugin, which monitors the iterations and reacts to what's happening. 

A typical pattern for an iterationListener would be asking it to do something every two to five iterations. For example, you might ask it to print the error associated with your net's latest guess. You might ask it to plot either the latest weight distribution or the latest reconstructions your RBM imagines match the input data or the activations in the net itself. In addition, an iterationListener logs activity associated with the iteration, and helps you debug. 

        model.setListeners(Collections.singletonList((IterationListener) new ScoreIterationListener(listenerFreq)));

In this line of code, the ScoreIterationListener is passed the parameter specifying a number of iterations -- let's say you specify two -- and after every two iterations, it will print out the error or cost. (The higher the frequency, the more you slow things down).