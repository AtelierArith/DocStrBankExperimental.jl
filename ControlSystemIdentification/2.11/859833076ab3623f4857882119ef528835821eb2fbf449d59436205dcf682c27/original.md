```
predict(ARX::TransferFunction, d::InputOutputData)
```

One step ahead prediction for an ARX process.  The length of the returned prediction is `length(d) - max(na, nb)`

# Example:

```jldoctest
julia> predict(tf(1, [1, -1], 1), iddata(1:10, 1:10))
9-element Vector{Int64}:
  2
  4
  6
  8
 10
 12
 14
 16
 18
```
