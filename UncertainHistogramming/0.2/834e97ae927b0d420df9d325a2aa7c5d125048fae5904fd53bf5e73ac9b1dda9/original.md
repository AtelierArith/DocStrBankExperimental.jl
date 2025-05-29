```
eltype(::ContinuousHistogram)
```

`Base` overload for accessing the `eltype.`

```jldoctest
julia> eltype(GaussianHistogram())
Float64

julia> eltype(UniformHistogram{Float32}())
Float32
```
