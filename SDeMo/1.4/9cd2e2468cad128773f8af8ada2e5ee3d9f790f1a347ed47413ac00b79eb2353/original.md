```
noskill(labels::Vector{Bool})
```

Returns the confusion matrix for the no-skill classifier given a vector of labels. Predictions are made at random, with each class being selected by its proportion in the training data.
