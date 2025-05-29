```
trim(x; dims::Tuple, pad::Int)
```

`x`から`missingval(x)`を`dims`の軸に沿ってトリミングし、`x`のビューを返します。

# 引数

  * `x`: `Raster`または`RasterStack`。スタックの場合、ピクセルがトリミングされるためには、すべてのレイヤーが欠損値を持っている必要があります。

# キーワード

  * `dims`: デフォルトでは`dims=(XDim, YDim)`であり、トリミングは他のすべての次元に沿って欠損値を含まない`X`と`Y`の領域を保持します。
  * `pad`: トリミングされたサイズはすべての側面に`pad`でパディングされますが、配列の元の範囲を超えてパディングは追加されません。

`trim`は遅延評価であるため、`filename`および`suffix`キーワードは使用されません。

# 例

オーストラリアの生息地の異質性のトリミングされたレイヤーを作成します。

```jldoctest
using Rasters, RasterDataSources, Plots
layers = (:evenness, :range, :contrast, :correlation)
st = RasterStack(EarthEnv{HabitatHeterogeneity}, layers)

# おおよそオーストラリアを切り取る
ausbounds = X(100 .. 160), Y(-50 .. -10)
aus = st[ausbounds...]
a = plot(aus)

# 欠損値をトリミングしてプロット
b = plot(trim(aus))

savefig(a, "build/trim_example_before.png");
savefig(b, "build/trim_example_after.png"); nothing

# 出力

```

### `trim`の前:

![before trim](trim_example_before.png)

### `trim`の後:

![after trim](trim_example_after.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
