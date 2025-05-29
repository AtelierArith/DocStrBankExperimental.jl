```
support(spline::Spline) -> a, b
```

`spline`が`BSpline`の場合、Bスプラインが非ゼロである区間$[a,b]$を返します。それ以外の場合は、`support(basis(spline))`を返します。

# 例

```jldoctest
julia> basis = BSplineBasis(3, 0:5);

julia> spline = Spline(basis, ones(7));

julia> zerospline = Spline(basis, zeros(7));

julia> support(spline)
(0, 5)

julia> support(zerospline) # スプラインがどこでもゼロであっても
(0, 5)

julia> support(basis[4]) # BSplineの場合、実際のサポートを返す
(1, 4)
```
