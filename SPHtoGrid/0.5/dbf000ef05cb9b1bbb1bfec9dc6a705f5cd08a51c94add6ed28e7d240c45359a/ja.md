```
sphMapping( Pos, HSML, Bin_Quant;
            param::mappingParameters,
            kernel::AbstractSPHKernel,
            show_progress::Bool=true,
            parallel::Bool=false,
            reduce_image::Bool=true,
            filter_particles::Bool=true,
            dimensions::Int=2)
```

`Bin_Quant`のデータをグリッドにマッピングします。マッピングのパラメータは`param`で提供され、使用するカーネルは`kernel`で指定されます。

# 引数

  * `Pos`: 粒子位置を持つ行列 (3xNpart)。
  * `HSML`: 粒子のhsmlを持つ配列。
  * `Bin_Quant`: マッピングされる粒子量を持つ配列。
  * `kernel::AbstractSPHKernel`: 使用するカーネルオブジェクト。
  * `show_progress::Bool=true`: 進行状況バーを表示する。
  * `parallel::Bool=true`: 複数のプロセッサで実行する。
  * `reduce_image::Bool=true`: 重みを適用する必要があるかどうか。[`part_weight_one`](@ref)および[`part_weight_physical`](@ref)の場合は`false`に設定します。
  * `filter_particles::Bool=true`: 実際に画像に含まれている粒子を見つける。
  * `dimensions::Int=2`: マッピング次元の数 (2 = グリッドに、3 = キューブに)。
