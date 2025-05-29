```
is_cyclotomic_polynomial_with_data(p::PolyRingElem{T}) where T -> Bool, Int
```

`p` がサイクロトミックであるかどうかと、どのサイクロトミック多項式であるかを含むタプルを返します。

# 例

```jldoctest
julia> _, b = cyclotomic_field_as_cm_extension(12)
(Relative number field of degree 2 over maximal real subfield of cyclotomic field of order 12, z_12)

julia> is_cyclotomic_polynomial_with_data(minpoly(b))
(false, -1)

julia> is_cyclotomic_polynomial_with_data(absolute_minpoly(b))
(true, 12)
```
