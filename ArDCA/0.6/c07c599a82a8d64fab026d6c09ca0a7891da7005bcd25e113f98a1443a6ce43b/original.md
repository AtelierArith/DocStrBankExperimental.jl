```
loglikelihood(x0::AbstractVector{T}, arnet::ArNet) where {T<:Integer}
```

Return the loglikelihood of sequence `x0` encoded in integer values in `1:q` under the model `arnet``. 
