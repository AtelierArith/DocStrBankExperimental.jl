```
histogram_irregular(x::AbstractVector{<:Real}; rule::Str="bayes", grid::String="regular", right::Bool=true, greedy::Bool=true, maxbins::Int=-1, support::Tuple{Real,Real}=(-Inf,Inf), use_min_length::Bool=false, logprior::Function=k->0.0, a::Real=1.0)
```

ベイズ確率、ペナルティ付き尤度、またはLOOCVに基づく基準の最適化に基づいて不規則なヒストグラムを作成します。指定されたルールに対応する最適な区間を持つStatsBase.Histogramオブジェクトを返します。

# 引数

  * `x`: ヒストグラムを構築するための1Dデータベクター。

# キーワード引数

  * `rule`: 最適なビンの数を決定するために使用される基準。デフォルトはSimensen et al. (2025)のベイズ法です。
  * `grid`: 最も細かいメッシュをどのように構築するかを示す文字列。オプションは、各ユニークデータポイントをグリッドポイントとして使用する`"data"`、細かい正規グリッドを構築する`"regular"`（デフォルト）、およびサンプル分位数に基づいてグリッドを構築する`"quantile"`です。
  * `right`: 描画された区間が右包含であるべきかどうかを示すブール値。デフォルトは`true`です。
  * `greedy`: Rozenholc et al. (2006)の貪欲ビニング戦略を動的プログラミングアルゴリズムを実行する前に使用するかどうかを示すブール値。デフォルトは`true`です。このキーワードが`false`に設定されている場合、大規模データセットではアルゴリズムが非常に遅くなる可能性があります。
  * `maxbins`: 最適化基準によって考慮される最大ビン数。`grid`が"regular"または"quantile"に設定されている場合のみ使用されます。デフォルトは`maxbins=min(4*n/log(n)^2, 1000)`です。指定された引数が正の整数でない場合、デフォルト値が使用されます。
  * `support`: ヒストグラム推定のサポートを指定するタプル。最初の要素が-Infの場合、`minimum(x)`が最も左のカットポイントとして取られます。同様に、2番目の要素が`Inf`の場合、最も右のカットポイントは`maximum(x)`です。デフォルト値は`(-Inf, Inf)`で、データのサポートを推定します。
  * `use_min_length`: ヒストグラムの最小ビン長に制限を課すかどうかを示すブール値。`true`に設定すると、許可される最小ビン長は`(maximum(x)-minimum(x))/n*log(n)^(1.5)`に設定されます。
  * `logprior`: ビンの数kのための非正規化対数事前分布。均一事前がデフォルトです。`rule="bayes"`のときのみ使用されます。
  * `a`: ベイズ不規則ヒストグラムモデルにおけるディリクレ濃度パラメータ。指定された値が正の実数でない場合、デフォルト値（5.0）に設定されます。`rule="bayes"`のときのみ使用されます。

# 返り値

  * `H`: 密度に対応する重みを持つStatsBase.Histogramオブジェクト。例えば、`:isdensity`がtrueに設定されます。

# 例

```
julia> x = [0.037, 0.208, 0.189, 0.656, 0.45, 0.846, 0.986, 0.751, 0.249, 0.447]
julia> H1 = histogram_irregular(x)
julia> H2 = histogram_irregular(x; grid="quantile", support=(0.0, 1.0), logprior=k->-log(k), a=sqrt(10))
```

...
