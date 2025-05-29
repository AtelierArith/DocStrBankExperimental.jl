```
WithIterationsDo(f=x->@info("iterations: $x"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithIterationsDo(x->put!(my_channel, x))`. 

Call `f(x)`, where `x` is the current number of model iterations (generally more than the number of control cycles). If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
