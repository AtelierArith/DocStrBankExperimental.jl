```
dput!(res::Vector{ComplexF64}, p1^2, p2^2, p3^2, p4^2, (p1+p2)^2, (p2+p3)^2, 
m1^2, m2^2, m3^2, m4^2)
```

すべての四点係数を長さ240の事前割り当て配列`res`に返します。

[`dget`](@ref)および[`dgetsym`](@ref)も参照してください。
