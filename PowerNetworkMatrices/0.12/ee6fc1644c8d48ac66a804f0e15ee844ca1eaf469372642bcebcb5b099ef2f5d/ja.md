```julia
PTDF(sys; dist_slack, reduce_radial_branches, kwargs...)

```

システムからPTDF行列を構築します。戻り値はバス番号でインデックス付けされたPTDF配列です。`dist_slack`と`reduce_radial_branches`のキーワード引数は、関数内で必要なため明示的に言及されています。

# 引数

  * `sys::PSY.System`:       行列が構築されるPSYシステム

# キーワード引数

  * `dist_slack::Vector{Float64}=Float64[]`:       分散スラックバスとして使用される重みのベクトル。       分散スラックベクトルはバスの数と同じ長さでなければなりません
  * `reduce_radial_branches::Bool=false`:       Trueの場合、行列はすべての放射状ブランチと葉バスを無視して評価されます（オプション、デフォルト値はfalseです）
