```
wsum!(R::AbstractArray, A::AbstractArray,
      w::AbstractVector, dim::Int;
      init::Bool=true)
```

Compute the weighted sum of `A` with weights `w` over the dimension `dim` and store the result in `R`. If `init=false`, the sum is added to `R` rather than starting from zero.
