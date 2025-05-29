```
WithModelDo(f=x->@info("model: $x"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithModelDo(x->put!(my_channel, x))`. 

Call `f(x)`, where `x` is the model associated with the training machine; `f` may mutate `x`, as in `f(x) = (x.learning_rate *= 0.9)`. If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
