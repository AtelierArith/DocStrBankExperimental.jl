```
mass_density(pos::Matrix{<:Real}, mass::Vector{<:Real}; 
             kernel::AbstractSPHKernel=Cubic(Float64, 3),
             Nneighbors::Integer=32,
             boxsize::Vector{<:Real}=zeros(3),
             verbose::Bool=false)
```

任意の粒子分布の密度をSPH法を使用して計算します。隣接粒子の検索は（周期的）BallTreeを使用して行われます。密度は入力単位で計算されるため、入力単位がcgsでない場合はcgs単位への追加の単位変換が必要です。

## 引数:

  * `pos`: 物理コード単位での粒子位置。
  * `mass`: 物理コード単位での粒子質量。

## キーワード引数

  * `kernel::AbstractSPHKernel=Cubic(Float64, 3)`: 密度推定に使用するSPHカーネル。 [SPHKernels.jl](https://github.com/LudwigBoess/SPHKernels.jl) の任意のカーネルで動作します。
  * `Nneighbors::Integer=32`: 密度推定に使用する隣接粒子の数。
  * `boxsize::Vector{<:Real}=zeros(3)`: 各次元のボックスサイズ。周期的境界条件に使用されます。ゼロに設定すると、非周期的境界条件が仮定されます。
  * `verbose::Bool=false`: trueに設定すると、進捗報告と進捗バーが表示されます。

## 戻り値

  * `rho`: 入力単位での粒子位置での質量密度。
  * `hsml`: 入力単位での各粒子のスムージング長。

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を減少させる: `false`
