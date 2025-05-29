```
isplateau(i, x[, w=1; strict=true]) -> Union{Missing,Bool}
```

`i`が`x`の中でプレートーであるかをテストします。プレートーは、連続する等しい（`==`）極値を持ち、その前後にそれより小さい値がある最大値または最小値として定義されます。`i`が`x`の最後のインデックスである場合は`false`を返します。

関連情報: [`ismaxima`](@ref), [`isminima`](@ref)
