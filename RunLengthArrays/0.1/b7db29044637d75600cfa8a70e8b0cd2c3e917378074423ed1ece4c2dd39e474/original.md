```
runs(arr::RunLengthArray{N,T})
```

Returns a `Array{N,1}` type containing the length of each run in the run-length array.

```julia
x = RunLengthArray{Int,String}(["X", "X", "X", "O", "O"])
@assert runs(x) == Int[3, 2]
```

To get a list of the values, use `values`.
