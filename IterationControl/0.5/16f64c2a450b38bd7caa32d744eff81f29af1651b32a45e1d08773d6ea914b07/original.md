```
WithNumberDo(f=n->@info("number: $n"), stop_if_true=false, stop_message=nothing)
```

An iteration control, as in, `WithNumberDo(n->put!(my_channel, n))`. 

Call `f(n + 1)`, where `n` is the number of complete control cycles. of the control (so, `n = 1, 2, 3, ...`, unless control is wrapped in a [`IterationControl.skip`](@ref))`.

If `stop_if_true` is `true`, then trigger an early stop if the value returned by `f` is `true`, logging the `stop_message` if specified. 
