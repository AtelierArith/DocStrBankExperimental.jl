```
eltype(::ContinuousHistogram)
```

`Base` のオーバーロードで `eltype` にアクセスします。

```jldoctest
julia> eltype(GaussianHistogram())
Float64

julia> eltype(UniformHistogram{Float32}())
Float32
```
