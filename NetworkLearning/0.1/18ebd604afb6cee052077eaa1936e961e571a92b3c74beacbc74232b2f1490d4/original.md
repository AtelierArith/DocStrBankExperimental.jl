```
add_adjacency!(model, Av)
```

Function that adds or, creates and then adds, adjacency objects contained in a vector `Av` to a network  learning `model`. The method is used in 'ouf-of-graph' learning i.e. the training data is not used in  the predictions for new samples. In such circumstances, the adjacency structures - graphs, matrices etc.  pertinent to the new observations have to be created either using the same functions used in training or,  separately supplied, so that relational variables can be created.
