```
map_it(pos_in, hsml, mass, rho, bin_q, weights, RM=nothing;
       param::mappingParameters,
       kernel::AbstractSPHKernel=WendlandC6(2), 
       snap::Integer=0, 
       units::AbstractString="", 
       image_prefix::String="dummy",
       reduce_image::Bool=true, 
       parallel=true,
       calc_mean::Bool=true, show_progress::Bool=true,
       sort_z::Bool=false,
       stokes::Bool=false,
       projection="xy")
```

小さなヘルパー関数で、位置をコピーし、粒子をマッピングし、fitsファイルを保存します。

# 引数

  * `pos_in`: 粒子位置の行列 (3xNpart)
  * `hsml`: 粒子のhsmlを含む配列
  * `mass`: 粒子の質量を含む配列
  * `rho`: 粒子の密度を含む配列
  * `bin_q`: マッピングされる粒子の量を含む配列
  * `weights`: 重みを含む配列。デフォルトは密度加重
  * `param`: このマップのための`mappingParameters`
  * `kernel`: マッピングに使用される`AbstractSPHKernel`
  * `units`: 単位文字列はFITSファイルに保存されます
  * `image_prefix`: 保存するファイルの名前（`.fits`ファイルの拡張子なし）
  * `reduce_image`: 重みを適用する必要があるかどうか。[`part_weight_physical`](@ref)の場合は`false`に設定
  * `parallel`: 複数のプロセッサで実行します。
  * `calc_mean`: 視線に沿った平均値を計算します。`false`に設定すると、粒子はその`bin_q`が0より大きい場合のみ寄与します。
  * `show_progress`: 進行状況バーを表示
  * `sort_z`: 粒子を視線方向に従ってソートします。偏光マッピングに必要です。
  * `stokes`: 偏光角のファラデー回転を考慮するためにストークスパラメータをマッピングしている場合は`true`に設定します。
  * `projection`: 位置が回転する平面。3つのオイラー角（[°]単位）の配列でも可能（まだ使用されていません！）
