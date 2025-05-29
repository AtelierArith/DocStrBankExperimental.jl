```
WithMachineDo(f=x->@info("machine: $x"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithMachineDo(x->put!(my_channel, x))`. 

Call `f(x)`, where `x` is the training machine in its current state. If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
