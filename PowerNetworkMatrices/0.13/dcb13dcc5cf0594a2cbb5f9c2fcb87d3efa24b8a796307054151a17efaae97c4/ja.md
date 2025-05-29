```julia
VirtualLODF(sys; reduce_radial_branches, kwargs...)

```

システムからVirtual LODF行列を構築します。返されるのは空のキャッシュを持つVirtualLODF構造体です。

# 引数

  * `sys::PSY.System`:       行列が構築されるPSYシステム

# キーワード引数

  * `reduce_radial_branches::Bool=false`:       Trueの場合、行列はすべての放射状ブランチとリーフバスを無視して評価されます（オプション、デフォルト値はfalse）
  * `kwargs...`:       VirtualPTDFによって使用される他のキーワード引数
