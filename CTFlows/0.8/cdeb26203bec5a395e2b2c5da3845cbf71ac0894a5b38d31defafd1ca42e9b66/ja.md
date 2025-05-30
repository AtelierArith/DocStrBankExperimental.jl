Lieおよびポアソン括弧のためのマクロ

# 例

```@example
julia> H0 = (t, x, p) -> 0.5*(x[1]^2+x[2]^2+p[1]^2)
julia> H1 = (t, x, p) -> 0.5*(x[1]^2+x[2]^2+p[2]^2)
julia> @Lie {H0, H1}(1, [1, 2, 3], [1, 0, 7]) autonomous=false
#
julia> H0 = (x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[1]^2+v)
julia> H1 = (x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[2]^2+v)
julia> @Lie {H0, H1}([1, 2, 3], [1, 0, 7], 2) variable=true
#
```
