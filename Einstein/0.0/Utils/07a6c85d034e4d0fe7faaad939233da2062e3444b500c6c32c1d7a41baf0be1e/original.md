```
barycentric_interpolate(x::TF, points::AbstractVector{TF}, values::AbstractVector{TFC}, weights::Vector{TF}) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
```

Evaluate the value of the barycentric interpolation formula with nodes `points`, function values `values` and barycentric weights `weights` at point `x`.

# References

  * [chebfun/@chebtech2/bary.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/bary.m)
  * [Berrut2004](@citet*)
