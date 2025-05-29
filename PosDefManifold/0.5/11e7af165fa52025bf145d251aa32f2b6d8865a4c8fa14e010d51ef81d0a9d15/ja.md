```
randChi²(df::Int)
```

**エイリアス**: `randχ²`

`df` 自由度の *カイ二乗* 分布に従う乱数変数を生成します。

`df`>=20 の場合は *ウィルソン–ヒルフェルティ変換* を使用します - [カイ二乗分布](https://en.wikipedia.org/wiki/Chi-squared_distribution) を参照してください。

**例**

```julia
using Plots, PosDefManifold
chi=[randχ²(2) for i=1:10000]
histogram(chi) # Plots パッケージが必要です。プロットのバックエンドを確認してください。
```
