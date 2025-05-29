```
getindex(T::ITensor, ivs...)
```

Get the specified element of the ITensor, using a list of `IndexVal`s or `Pair{<:Index, Int}`.

# Example

```julia
i = Index(2; tags = "i")
A = ITensor(2.0, i, i')
A[i => 1, i' => 2] # 2.0, same as: A[i' => 2, i => 1]
```
