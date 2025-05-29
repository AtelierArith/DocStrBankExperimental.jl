```
sphMapping( Pos::Array{<:Real}, HSML::Array{<:Real}, M::Array{<:Real}, 
            Rho::Array{<:Real}, Bin_Quant::Array{<:Real}, 
            Weights::Array{<:Real}=Rho;
            param::mappingParameters,
            kernel::AbstractSPHKernel,
            show_progress::Bool=true,
            parallel::Bool=false,
            reduce_image::Bool=true,
            return_both_maps::Bool=false,
            filter_particles::Bool=true,
            dimensions::Int=2,
            calc_mean::Bool=false)
```

`Bin_Quant`のデータをグリッドにマッピングします。マッピングのパラメータは`param`で供給され、使用するカーネルは`kernel`で指定されます。

# 引数

  * `Pos`: 粒子の位置を持つ行列 (3xNpart)
  * `HSML`: 粒子のhsmlを持つ配列
  * `M`: 粒子の質量を持つ配列
  * `Rho`: 粒子の密度を持つ配列
  * `Bin_Quant`: マッピングされる粒子の量を持つ配列
  * `Weights`: 重みを持つ配列。デフォルトは密度加重
  * `param`: このマップのための`mappingParameters`
  * `kernel`: マッピングに使用される`AbstractSPHKernel`
  * `show_progress`: 進行状況バーを表示
  * `parallel`: 複数のプロセッサで実行
  * `reduce_image`: 重みを適用する必要があるかどうか。[`part_weight_physical`](@ref)のために`false`に設定
  * `return_both_maps`: 完全な画像配列を返します。サブファイルの並列マッピングで使用
  * `filter_particles`: 実際に画像に含まれている粒子を見つける
  * `dimensions`: マッピングの次元数 (2 = グリッドに, 3 = キューブに)
  * `calc_mean`: 視線に沿った平均値を計算します。`false`に設定すると、粒子はその`Bin_Quant`が0より大きい場合のみ寄与します
