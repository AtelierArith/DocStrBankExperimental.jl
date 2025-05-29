```julia
LODF(sys; reduce_radial_branches, kwargs...)

```

システムからLODF行列を構築します。`reduce_radial_branches`のキーワード引数は、関数内で必要なため明示的に言及されています。

# 引数

  * `sys::PSY.System`:       電力システム

# キーワード引数

  * `reduce_radial_branches::Bool=false`:       Trueの場合、行列はすべての放射状ブランチとリーフバスを無視して評価されます（オプション、デフォルト値はfalseです）
