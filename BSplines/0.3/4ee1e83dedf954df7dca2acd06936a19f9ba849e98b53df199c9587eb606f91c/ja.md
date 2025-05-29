```
order(spline::Spline)
order(basis::BSplineBasis)
```

スプラインまたはBスプライン基底の次数を返します。

# 例

```jldoctest
julia> order(BSplineBasis(3, 0:5))
3

julia> order(BSplineBasis(4, [1.0, 1.5, 2.5, 4.0]))
4
```
