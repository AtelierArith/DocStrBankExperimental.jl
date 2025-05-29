線形ガウスCPDは、常にノーマルを返します

```
ターゲットとすべての親がFloat64に変換できる（つまり、数値である）と仮定します。

P(x|parents(x)) = Normal(μ=a×parents(x) + b, σ)
```
