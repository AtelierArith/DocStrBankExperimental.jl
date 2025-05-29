```
B, flags = pmf(A; ωₘ, slope, dhₘ, dh₀, cellsize, adjust, erode)
```

*Zhang et al. (2003)* [^zhang2003] による進行形形態フィルタを `A` に適用します。

# 出力

  * `B::Array{T,2}` 最大許容値
  * `flags::Array{Float64,2}` フィルタリングされた場合のウィンドウサイズを持つ配列、フィルタリングされていない場合はゼロ。

その後、`A` の結果マスクを `A .<= B` または `flags .== 0.` によって取得できます。

# 引数

  * `A::Array{T,2}` 入力配列
  * `ωₘ::Real=20.` 最大ウィンドウサイズ [m]
  * `slope::Real=0.01` 地形の傾斜 [m/m]
  * `dhₘ::Real=2.5` 最大標高閾値 [m]
  * `dh₀::Real=0.2` 初期標高閾値 [m]
  * `cellsize::Real=1.` セルサイズ [m]

[^zhang2003]: Zhang, Keqi, Shu-Ching Chen, Dean Whitman, Mei-Ling Shyu, Jianhua Yan, and Chengcui Zhang. “A Progressive Morphological Filter for Removing Nonground Measurements from Airborne LIDAR Data.” IEEE Transactions on Geoscience and Remote Sensing 41, no. 4 (2003): 872–82. [https://doi.org/10.1109/TGRS.2003.810682](https://doi.org/10.1109/TGRS.2003.810682).
