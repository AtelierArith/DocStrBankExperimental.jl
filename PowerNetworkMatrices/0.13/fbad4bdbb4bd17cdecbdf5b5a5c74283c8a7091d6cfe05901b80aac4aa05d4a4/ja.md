```julia
VirtualLODF(
    branches,
    buses;
    tol,
    max_cache_size,
    persistent_lines,
    radial_network_reduction
)

```

ブランチとバスのグループからLODF行列を構築します。返されるのは、空のキャッシュを持つVirtualLODF構造体です。

# 引数

  * `branches`:       システムのACブランチのベクター。
  * `buses::Vector{PSY.ACBus}`:       システムのバスのベクター。

# キーワード引数

  * `tol::Float64 = eps()`:       スパース化およびドロップする値に関連する許容誤差。
  * `max_cache_size::Int`:       MiB単位の最大キャッシュサイズ（MAX*CACHE*SIZE_MiBとして初期化）。
  * `persistent_lines::Vector{String}`:       VirtualPTDFが作成されるとすぐに評価される行（空の文字列ベクターとして初期化）。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチと葉バスを含む構造体。
