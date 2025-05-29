```
bounds(itp::AbstractInterpolation)
```

`itp`のドメインの`bounds`を各座標の`(min, max)`ペアのタプルとして返します。これは例で説明するのが最適です：

```jldoctest
julia> itp = interpolate([1 2 3; 4 5 6], BSpline(Linear()));

julia> bounds(itp)
((1, 2), (1, 3))

julia> data = 1:3;

julia> knots = ([10, 11, 13.5],);

julia> itp = interpolate(knots, data, Gridded(Linear()));

julia> bounds(itp)
((10.0, 13.5),)
```
