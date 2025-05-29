```
not(z::BoolExpr)
¬z
```

`z`の論理否定を返します。

注意: 単項演算子をブロードキャストするには、構文`.¬z`が必要であり、これは新しいJuliaユーザーには混乱を招く可能性があります。便利のために`¬(z::Array{BoolExpr})`を定義します。

```julia
    @satvariable(z[1:n], Bool)
    ¬z  # map(¬, z)の構文糖
    .¬z # これも有効
```
