```
WithTrainingLossesDo(f=v->@info("training: $v"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithTrainingLossesDo(v->put!(my_losses, last(v))`. 

Call `f(training_losses)`, where `training_losses` is the vector of most recent batch of training losses.

If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
