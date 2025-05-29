```
(E::EllipticCurve)(coords::Vector; check::Bool = true)
```

Return the point $P$ of $E$ with coordinates specified by `coords`, which can be either affine coordinates (`length(coords) == 2`) or projective coordinates (`length(coords) == 3`).

Per default, it is checked whether the point lies on $E$. This can be disabled by setting `check = false`.

# Examples

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> E([1, -2])
(1 : -2 : 1)

julia> E([2, -4, 2])
(1 : -2 : 1)
```
