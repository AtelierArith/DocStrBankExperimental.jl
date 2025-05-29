```
rand(pd::MarginalScalingModel, d::AbstractVector{<:Real}, n::Int=1, ; tags::AbstractVector{<:AbstractString}=String[], x::AbstractVector{<:Real}=Float64[])
```

Generate a random sample of size `n` for duration vector `d` from the scaling model `pd`.

### Details

Duration tags and time vector can be provided with the keyword argument `tags` and `x` respectively. 
