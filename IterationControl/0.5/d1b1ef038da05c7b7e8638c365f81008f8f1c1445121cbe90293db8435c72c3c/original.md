```
Callback(f=_->nothing, stop_if_true=false, stop_message=nothing, raw=false)
```

An iteration control, as in, `Callback(m->put!(v, my_loss_function(m))`. 

Call `f(IterationControl.expose(m))`, where `m` is the object being iterated, unless `raw=true`, in which case call `f(m)` (guaranteed if `expose` has not been overloaded.) If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
