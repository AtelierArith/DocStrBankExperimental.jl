```
AbstractCovariance{T}
```

すべての共分散関数（特異または非特異）のスーパタイプです。

## 例

```jldoctest
julia> Covariance{Float64}<:AbstractCovariance{Float64}
true

julia> SingularCovariance{Int64}<:AbstractCovariance{Int64}
true
```
