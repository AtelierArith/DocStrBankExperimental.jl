```
colorview(C, gray1, gray2, ...) -> imgC
```

数値/グレースケール画像 `gray1`, `gray2` などを、要素型 `C<:Colorant` の配列 `imgC` の別々のカラーチャンネルに結合します。

便利なことに、定数 `zeroarray` は、すべての要素がゼロの一致したサイズの配列を埋めます。

# 例

```julia
imgC = colorview(RGB, r, zeroarray, b)
```

これは、赤チャンネルに `r`、青チャンネルに `b`、緑チャンネルには何もない画像を作成します。

関連項目: [`StackedView`](@ref).
