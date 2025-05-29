```
li0(z::Number)
```

数値 $z$ の 0 次ポリログarithm $\operatorname{Li}_0(z) = z/(1-z)$ を返します。$z$ の型は `Number` です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li0(0.25)
0.3333333333333333

julia> li0(BigFloat("0.25"))
0.3333333333333333333333333333333333333333333333333333333333333333333333333333348
```
