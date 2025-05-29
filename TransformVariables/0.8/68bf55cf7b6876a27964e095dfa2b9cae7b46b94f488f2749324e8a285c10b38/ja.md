```julia
logjac_forwarddiff(f, x; handleNaN, chunk, cfg)

```

`f`の`x`におけるログヤコビアン行列式を`ForwardDiff`を使用して計算します。

# 注意

`f`は、実数のベクトルから同じ長さのベクトルへの全単射である必要があります。

`handleNaN = true`（デフォルト）である場合、`NaN`のログヤコビアンは`-Inf`に変換されます。
