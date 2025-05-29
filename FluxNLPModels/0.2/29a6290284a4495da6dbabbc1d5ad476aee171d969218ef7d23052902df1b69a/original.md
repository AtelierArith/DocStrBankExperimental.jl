```
minibatch_next_train!(nlp::AbstractFluxNLPModel)
```

Selects the next minibatch from `nlp.training_minibatch_iterator`.   Returns the new current status of the iterator `nlp.current_training_minibatch`. `minibatch_next_train!` aims to be used in a loop or method call. if return false, it means that it reach the end of the mini-batch
