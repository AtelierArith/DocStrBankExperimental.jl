```
minibatch_next_test!(nlp::AbstractFluxNLPModel)
```

Selects the next minibatch from `nlp.test_minibatch_iterator`.   Returns the new current status of the iterator `nlp.current_test_minibatch`. `minibatch_next_test!` aims to be used in a loop or method call. if return false, it means that it reach the end of the mini-batch
