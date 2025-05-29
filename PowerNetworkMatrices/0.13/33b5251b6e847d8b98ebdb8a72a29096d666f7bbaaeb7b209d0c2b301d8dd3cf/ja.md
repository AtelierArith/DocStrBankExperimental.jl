```julia
PTDF(
    branches,
    buses;
    dist_slack,
    linear_solver,
    tol,
    radial_network_reduction
)

```

ブランチとバスのグループからPTDF行列を構築します。返されるのは、バス番号でインデックス付けされたPTDF配列です。

# 引数

  * `branches`:       システムACブランチのベクター
  * `buses::Vector{PSY.ACBus}`:       システムバスのベクター

# キーワード引数

  * `dist_slack::Vector{Float64}`:       分散スラックバスとして使用される重みのベクター。       分散スラックベクターはバスの数と同じ長さでなければなりません
  * `linear_solver::String`:       使用する線形ソルバー。オプションは「Dense」、「KLU」、および「MKLPardiso」です
  * `tol::Float64`:       PTDF行列のエントリを排除するための許容誤差（デフォルトはeps()）
  * `radial_network_reduction::RadialNetworkReduction`:       maを評価する際に削除された放射状ブランチと葉バスを含む構造
