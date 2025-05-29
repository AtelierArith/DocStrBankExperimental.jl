```
WithLossDo(f=x->@info("loss: $x"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithLossDo(x->put!(my_losses, x))`. 

Call `f(loss)`, where `loss` is current loss.

If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
