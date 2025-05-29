```
randobs(data, [n])
```

Pick a random observation or a batch of `n` random observations from `data`. For this function to work, the type of `data` must implement [`numobs`](@ref) and [`getobs`](@ref).
