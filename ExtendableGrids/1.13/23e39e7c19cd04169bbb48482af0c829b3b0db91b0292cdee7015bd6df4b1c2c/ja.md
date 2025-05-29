```julia
mutable struct BinnedPointList{T}
```

ビン付きポイントリスト構造体は、既存のポイントを迅速にチェックすることを可能にします。

これは、挿入されたポイントを特定するためのパフォーマンスを、単純な線形検索よりも向上させます。

一方で、実装はまだかなり単純です - 固定数のビンを持つ立方体ビニング領域を動的に維持します。

おそらく、木構造に基づく適応的手法（オクトリーのような）は、より効率的ですが、実装は難しくなるでしょう。

理想的な世界では、動的なドロネー三角形分割を維持し、これがメッシュ生成の出発点となることができるでしょう。

  * `dim::Int32`: 空間次元
  * `tol::Any`: ポイント距離の許容範囲。tol（ユークリッド距離）よりも近いポイントは特定され、つまり最初に挿入されたものに統合されます。
  * `binning_region_min::Vector`: "すべてのビンの合併がビニング領域であり、これはその2つのコーナーによって定義される立方体です。挿入されたポイントに応じて動的に計算されます。
  * `binning_region_max::Vector`
  * `binning_region_increase_factor::Any`: ビニング領域の増加係数（ビン付きポイントの座標によって定義される立方体に関して）
  * `points::ElasticArrays.ElasticArray{T, 2, M, V} where {T, M, V<:DenseVector{T}}`: 実際のポイントリスト
  * `bins::Array{Vector{Int32}}`: ビンはポイントリスト内のポイントのインデックスのベクトルです。これらを次元数の配列に格納し、長さは「number*of*directional_bins^dim」となります。
  * `number_of_directional_bins::Int32`: 各空間次元のビンの数
  * `unbinned::Vector{Int32}`: 一部のポイントはビニング領域の外に落ちます。これらを未ビンポイントインデックスのベクトルに収集します。
  * `num_allowed_unbinned_points::Int32`: 再ビンニングなしで許容される未ビンポイントの数
  * `max_unbinned_ratio::Any`: ポイントリスト内の未ビンポイントの最大比率
  * `current_bin::Vector{Int32}`: 現在のポイントビンのストレージ
