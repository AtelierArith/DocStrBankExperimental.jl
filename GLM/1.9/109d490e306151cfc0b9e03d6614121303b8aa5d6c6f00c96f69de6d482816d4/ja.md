```
fit(GeneralizedLinearModel, formula, data,
    distr::UnivariateDistribution, link::Link = canonicallink(d); <keyword arguments>)
fit(GeneralizedLinearModel, X::AbstractMatrix, y::AbstractVector,
    distr::UnivariateDistribution, link::Link = canonicallink(d); <keyword arguments>)
```

データに一般化線形モデルをフィットします。

最初のメソッドでは、`formula` は [StatsModels.jl `Formula` オブジェクト](https://juliastats.org/StatsModels.jl/stable/formula/) でなければならず、`data` はテーブル（[Tables.jl](https://tables.juliadata.org/stable/) 定義、例えばデータフレーム）でなければなりません。2番目のメソッドでは、`X` は独立変数の値を列に持つ行列でなければならず（必要に応じて切片を含む）、`y` は従属変数の値を持つベクトルでなければなりません。どちらの場合も、`distr` は分布を指定し、`link` はリンク関数を指定することができます（省略した場合、`distr` のための標準リンクとして取られます。組み込みリンクのリストについては [`Link`](@ref) を参照してください）。

# キーワード引数

  * `dropcollinear::Bool=true`: `lm` がフルランク未満のモデル行列を受け入れるかどうかを制御します。`true`（デフォルト）の場合、冗長な線形依存列の係数は `0.0` となり、関連するすべての統計は `NaN` に設定されます。通常、線形依存列のセットから最後のものが冗長として特定されます（ただし、冗長として特定される列の正確な選択は保証されません）。
  * `dofit::Bool=true`: モデルがフィットされるかどうかを決定します。
  * `wts::Vector=similar(y,0)`: 観測の事前頻度（別名ケース）重み。これらの重みは、各観測をその重みと等しい回数だけ繰り返すことに相当します。この解釈は等しい点推定を与えますが、他のソフトウェアのデフォルトである解析的（別名逆分散）重みや確率的（別名サンプリング）重みとは異なる標準誤差を与えることに注意してください。重み付けなしを示すために長さ0にすることができます（デフォルト）。
  * `offset::Vector=similar(y,0)`: `Xβ` に追加されるオフセットで、`eta` を形成します。長さ0にすることができます。
  * `verbose::Bool=false`: 各イテレーションの収束情報を表示します。
  * `maxiter::Integer=30`: 収束を達成するために許可される最大イテレーション数。
  * `atol::Real=1e-6`: 収束は、偏差の相対変化が `max(rtol*dev, atol)` より小さいときに達成されます。
  * `rtol::Real=1e-6`: 収束は、偏差の相対変化が `max(rtol*dev, atol)` より小さいときに達成されます。
  * `minstepfac::Real=0.001`: 最小ラインステップ比。0と1の間でなければなりません。
  * `start::AbstractVector=nothing`: ベータの初期値。モデル行列の列数と同じ長さである必要があります。
