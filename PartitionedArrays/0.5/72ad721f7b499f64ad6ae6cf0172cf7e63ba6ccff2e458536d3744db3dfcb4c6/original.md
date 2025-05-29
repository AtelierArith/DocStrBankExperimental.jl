```
exchange!(rcv,snd,graph::ExchangeGraph) -> Task
```

In-place and fake*asynchronous version of [`exchange`](@ref). This function returns immediately and returns a task that produces `rcv` with the updated values. Use `fetch` to get the updated version of `rcv`. The input `rcv` can be allocated with [`allocate*exchange`](@ref).
