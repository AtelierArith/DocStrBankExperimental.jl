```
is_cyclotomic_polynomial(p::PolyRingElem{T}) where T -> Bool
```

`p` が巡回多項式であるかどうかを返します。

# 例

```jldoctest
julia> _, b = cyclotomic_field_as_cm_extension(12)
(Relative number field of degree 2 over maximal real subfield of cyclotomic field of order 12, z_12)

julia> is_cyclotomic_polynomial(minpoly(b))
false

julia> is_cyclotomic_polynomial(absolute_minpoly(b))
true
```
