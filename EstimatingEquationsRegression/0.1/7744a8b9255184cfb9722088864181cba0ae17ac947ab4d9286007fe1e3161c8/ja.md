```
fit(GeneralizedEstimatingEquationsModel, X, y, g, d, c, [l = canonicallink(d)]; <keyword arguments>)
```

一般化推定方程を使用してデータに一般化線形モデルを適合させます。 `X` と `y` はそれぞれ行列とベクトル、または式とデータフレームであることができます。 `g` はグループラベルを含むベクトルであり、グループ内の要素はデータ内で連続している必要があります。 `d` は `UnivariateDistribution` でなければならず、`c` は `CorStruct` で、`l` は提供されている場合は [`Link`](@ref) でなければなりません。

# キーワード引数

  * `cov_type::String`: パラメータの共分散推定のタイプ。デフォルトは "robust" で、他のオプションは "naive"、"md" (Mancl-DeRouen デビアス) および "kc" (Kauermann-Carroll デビアス) です。
  * `dofit::Bool=true`: モデルが適合されるかどうかを決定します。
  * `wts::Vector=similar(y,0)`: 実装されていません。

長さ 0 で重み付けなしを示すことができます（デフォルト）。

  * `offset::Vector=similar(y,0)`: `Xβ` に追加されるオフセットで、`eta` を形成します。長さ 0 であることができます。
  * `verbose::Bool=false`: 各イテレーションの収束情報を表示します。
  * `maxiter::Integer=100`: 収束を達成するために許可される最大イテレーション数。
  * `atol::Real=1e-6`: 収束は、`β` の相対変化が `max(rtol*dev, atol)` より小さいときに達成されます。
  * `rtol::Real=1e-6`: 収束は、`β` の相対変化が `max(rtol*dev, atol)` より小さいときに達成されます。
  * `start::AbstractVector=nothing`: ベータの開始値。モデル行列の列数と同じ長さである必要があります。
  * `fitcoef::Bool=true`: false の場合、係数を GLM 係数または提供された場合は `start` に等しく設定し、GEE イテレーションを使用せずに相関パラメータと分散を更新します。
  * `fitcor::Bool=true`: false の場合、相関パラメータをその開始値に等しく保持します。
  * `bccor::Bool=true`: false の場合、Kauermann-Carroll および Mancel-DeRouen の共分散を計算しません。
