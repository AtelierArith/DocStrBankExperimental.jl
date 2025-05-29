```
lacosmic(data::AbstractMatrix;
    noise=nothing,
    gain=1,
    background=0,
    readnoise=0,
    mask=falses(size(data)),
    sigma_clip=4.5,
    contrast=5,
    neighbor_thresh=0.3,
    maxiter=4,
    saturation_level=2^16,
    block_size=2)
```

ラプラシアンコスミックレイ検出（LACosmic）。このアルゴリズムは、[lacosmicx](https://github.com/cmccully/lacosmicx)で提示されたアルゴリズムを実装しています。返り値は、クリーンな画像と悪いピクセルマスクです。画像のクリーン化は中央値補間によって行われます。

# パラメータ

  * `noise` は、データノイズの事前に決定された推定値（分散の平方根）です。
  * `gain` は、データ数あたりの電子の画像ゲインです。
  * `background` は、事前に決定された画像の背景です。
  * `readnoise` は、画像の読み出しノイズ（電子）です。
  * `mask` は、入力の悪いピクセルマスクで、`true` は悪いピクセルを表します。
  * `sigma_clip` は、悪いピクセルをフラグ付けするためのラプラシアン信号対ノイズ比です。
  * `contrast` は、ラプラシアン画像と微細構造画像の比率で悪いピクセルをフラグ付けするために必要な最小コントラストです。
  * `neighbor_thresh` は、他のコスミックレイを囲むコスミックレイの検出限界の割合です。0と1の間の数である必要があります。
  * `maxiter` は、悪いピクセルを検出するために使用される最大反復回数です。
  * `saturation_level` は、電子の飽和値です。
  * `block_size` は、ラプラシアンフィルター画像のサブサンプリング係数です。

# 例

```jldoctest
julia> image = 100 .* randn(1001, 1001) .+ 1000;

julia> clean_image, mask = lacosmic(image, gain=4);
```

# 参考文献

> [van Dokkum, P.G. (2001)](https://ui.adsabs.harvard.edu/abs/2001PASP..113.1420V/abstract) - "ラプラシアンエッジ検出によるコスミックレイ除去"

