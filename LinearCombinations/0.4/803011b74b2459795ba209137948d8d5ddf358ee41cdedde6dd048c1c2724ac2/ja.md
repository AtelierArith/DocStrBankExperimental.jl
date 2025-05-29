```
LinearExtension{F}
```

この型は、与えられた型 `F` の線形拡張です。

# 例

```jldoctest
julia> const g = LinearExtension(uppercase)
LinearExtension(uppercase)

julia> g('x')
'X': ASCII/Unicode U+0058 (category Lu: Letter, uppercase)

julia> a = Linear('x' => 1, 'y' => 2); g(a; coeff = 3)
Linear{Char, Int64} with 2 terms:
6*'Y'+3*'X'
```
