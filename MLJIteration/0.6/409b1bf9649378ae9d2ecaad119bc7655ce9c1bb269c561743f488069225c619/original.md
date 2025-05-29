```
WithEvaluationDo(f=x->@info("evaluation: $x"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithEvaluationDo(x->put!(my_channel, x))`. 

Call `f(x)`, where `x` is the latest performance evaluation, as returned by `evaluate!(train_mach, resampling=..., ...)`. Not valid if `resampling=nothing`. If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
