```julia
VirtualPTDF(
    sys;
    dist_slack,
    reduce_radial_branches,
    kwargs...
)

```

システムから仮想PTDF行列を構築します。返されるのは、空のキャッシュを持つVirtualPTDF構造体です。

# 引数

  * `sys::PSY.System`:       行列が構築されるPSYシステム

# キーワード引数

  * `dist_slack::Vector{Float64}=Float64[]`:       分散スラックバスとして使用される重みのベクトル。       分散スラックベクトルは、バスの数と同じ長さでなければなりません
  * `reduce_radial_branches::Bool=false`:       Trueの場合、行列はすべての放射状ブランチと葉バスを無視して評価されます（オプション、デフォルト値はfalse）
  * `kwargs...`:       VirtualPTDFによって使用される他のキーワード引数
