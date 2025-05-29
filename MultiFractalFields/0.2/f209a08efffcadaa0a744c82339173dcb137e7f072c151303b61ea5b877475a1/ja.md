```
SingularCovariance{T}
```

特異共分散関数のスーパークラスです。

特異とは、分散 $\sigma^2 = \infty$ であることを意味します。

## 例

```jldoctest
julia> Log{Float64}<:SingularCovariance{Float64}
true
```
