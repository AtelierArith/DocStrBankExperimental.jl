```
li6(z::Complex)
```

複素数 $z$ の複素6次ポリログarithm $\operatorname{Li}_6(z)$ を返します。$z$ の型は `Complex` です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li6(1.0 + 1.0im)
0.996149796835317 + 1.0335544477237482im
```
