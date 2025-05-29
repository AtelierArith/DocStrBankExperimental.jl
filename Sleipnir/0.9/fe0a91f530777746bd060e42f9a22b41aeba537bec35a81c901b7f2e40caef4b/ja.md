```
apply_t_cumul_grad!(climate_2D_step::Climate2Dstep, S::Matrix{F}) where {F <: AbstractFloat}
```

正の度日（PDD）と標高行列 `S` に基づいて温度と降水量の勾配を適用し、`climate_2D_step` の気候データを更新します。

# 引数

  * `climate_2D_step::Climate2Dstep`: 温度、PDD、勾配、および基準高さを含む気候データ構造。
  * `S::Matrix{F}`: 標高の行列。

# 説明

この関数は、標高行列 `S` と基準高さの差に基づいて、それぞれの勾配を適用することによって `climate_2D_step` の温度とPDDフィールドを更新します。負のPDD値はゼロに切り捨てられます。さらに、関数は更新された温度値に基づいて雨と雪の割合を調整します。
