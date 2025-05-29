```
Covariance{T}
```

「真の」（非特異）共分散関数のスーパタイプです。

非特異とは、分散 $\sigma^2 < \infty$ を意味します。

## 例

```jldoctest
julia> Exponential{Float32}<:Covariance{Float32}
true

julia> Linear{Int16}<:Covariance{Int16}
true
```
