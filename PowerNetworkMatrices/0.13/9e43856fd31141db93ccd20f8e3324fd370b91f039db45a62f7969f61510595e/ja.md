```julia
VirtualPTDF(
    branches,
    buses;
    dist_slack,
    tol,
    max_cache_size,
    persistent_lines,
    radial_network_reduction
)

```

ブランチとバスのグループからPTDF行列を構築します。戻り値は空のキャッシュを持つVirtualPTDF構造体です。

# 引数

  * `branches`:       システムのACブランチのベクター。
  * `buses::Vector{PSY.ACBus}`:       システムのバスのベクター。

# キーワード引数

  * `dist_slack::Vector{Float64} = Float64[]`:       分散スラックバスとして使用される重みのベクター。       分散スラックベクターはバスの数と同じ長さでなければなりません。
  * `tol::Float64 = eps()`:       スパース化およびドロップする値に関連する許容誤差。
  * `max_cache_size::Int`:       MiB単位の最大キャッシュサイズ（MAX*CACHE*SIZE_MiBとして初期化）。
  * `persistent_lines::Vector{String}`:       VirtualPTDFが作成されるとすぐに評価される行（空の文字列ベクターとして初期化）。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチと葉バスを含む構造体。
