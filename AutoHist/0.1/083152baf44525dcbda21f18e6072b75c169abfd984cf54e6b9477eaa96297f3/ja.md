```
histogram_regular(x::AbstractVector{<:Real}; rule::Str="bayes", right::Bool=true, maxbins::Int=1000, support::Tuple{Real,Real}=(-Inf,Inf), logprior::Function=k->0.0, a::Union{Real,Function}=1.0)
```

ベイズ確率、ペナルティ付き尤度、またはLOOCVからの最適化基準に基づいて、通常のヒストグラムを作成します。提供された基準に対応する最適なビン数を持つ、通常のビンを持つStatsBase.Histogramオブジェクトを返します。

...

# 引数

  * `x`: ヒストグラムを構築するためのデータの1Dベクトル。

# キーワード引数

  * `rule`: 最適なビン数を決定するために使用される基準。デフォルトはSimensenら（2025）のベイズ法です。
  * `right`: 描画された区間が右包含であるかどうかを示すブール値。デフォルトは`true`です。
  * `maxbins`: 最適化基準によって考慮される最大ビン数。指定された引数が正の整数でない場合は無視されます。デフォルトは`maxbins=1000`です。
  * `support`: ヒストグラム推定のサポートを指定するタプル。最初の要素が-Infの場合、`minimum(x)`が最も左のカットポイントとして取られます。同様に、2番目の要素が`Inf`の場合、最も右のカットポイントは`maximum(x)`です。デフォルト値は`(-Inf, Inf)`で、データのサポートを推定します。
  * `logprior`: ビンの数kの非正規化対数事前分布。提供されたルールが`"bayes"`の場合のみ使用されます。デフォルトは一様事前です。
  * `a`: ベイズヒストグラムモデルにおけるディリクレ濃度パラメータを指定します。固定の正の数または異なるkの値に対してaₖを計算する関数のいずれかであることができます。提供されない場合はデフォルトで`1.0`です。提供された値が負の場合はデフォルトを使用します。

# 戻り値

  * `H`: 密度に対応する重みを持つStatsBase.Histogramオブジェクト。例えば、`:isdensity`がtrueに設定されています。

# 例

```
julia> x = [0.037, 0.208, 0.189, 0.656, 0.45, 0.846, 0.986, 0.751, 0.249, 0.447]
julia> H1 = histogram_regular(x)
julia> H2 = histogram_regular(x; logprior=k->-log(k), a=k->0.5*k)
```

...
