```
getindex(T::ITensor, I::Int...)
```

Get the specified element of the ITensor, using internal Index ordering of the ITensor.

# Example

```julia
i = Index(2; tags = "i")
A = ITensor(2.0, i, i')
A[1, 2] # 2.0, same as: A[i => 1, i' => 2]
```
