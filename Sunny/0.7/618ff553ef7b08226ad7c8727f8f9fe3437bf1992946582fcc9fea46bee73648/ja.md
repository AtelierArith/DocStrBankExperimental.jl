```
BinningParameters(binstart, binend, binwidth; covectors=I(4))
BinningParameters(binstart, binend; numbins, covectors=I(4))
```

これは、実験的非弾性中性子散乱データと互換性のある形式で4D平行六面体ヒストグラムを記述します。[`BinningParameters`](@ref)を[Mantidソフトウェア](https://www.mantidproject.org/)が理解できる形式に変換するには`generate_mantid_script_from_binning_parameters`を参照してください。また、Mantidの`.nxs`ファイルから[`BinningParameters`](@ref)をロードするには[`load_nxs`](@ref)を参照してください。

ヒストグラム軸の座標は、`covectors`行列の各行との`(q,ω)`の乗算によって指定され、`q`は[R.L.U.]で与えられます。デフォルトの`covectors`行列は単位行列であるため、デフォルトの軸は絶対単位で`(qx, qy, qz, ω)`です。

ビンニングスキームの規則は次のとおりです：

  * 最初のビンの左端は`binstart`から始まります
  * ビン幅は`binwidth`です
  * 最後のビンは`binend`を含みます
  * 「部分ビン」はなく、最後のビンには`binend`を超える値が含まれる場合があります。

`value`は、そのビンインデックスを計算することでビンに入れることができます：

```jl
    coords = covectors * value
    bin_ix = 1 .+ floor.(Int64, (coords .- binstart) ./ binwidth)
```
