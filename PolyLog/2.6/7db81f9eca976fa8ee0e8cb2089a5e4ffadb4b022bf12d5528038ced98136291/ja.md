```
li5(z::Complex)
```

複素数 $z$ の複素5次ポリログarithm $\operatorname{Li}_5(z)$ を返します。$z$ の型は `ComplexF` です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li5(1.0 + 1.0im)
0.9874666591701127 + 1.068441607107422im
```
