```
(mod::BaselineModel)(queries::Vector{String})
```

Computes a forward pass of the model on the given queries and returns either the logits or embeddings depending on whether or not the model was loaded with the head for classification.
