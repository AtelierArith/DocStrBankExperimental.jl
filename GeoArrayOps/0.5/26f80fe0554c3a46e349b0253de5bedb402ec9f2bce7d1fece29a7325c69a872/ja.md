```
B = smf(A; ω, slope, dhₘ, dh₀, cellsize)
```

*Pingel et al. (2013)* [^pingel2013] による単純な形態フィルタを `A` に適用します。

# 出力

  * `B::Array{Float64,2}` A のフィルタリングされたバージョン

# 引数

  * `A::Array{T,2}` 入力配列
  * `ω::Float64=18.` 最大ウィンドウサイズ [m]
  * `slope::Float64=0.01` 地形の傾斜 [m/m]
  * `cellsize::Float64=1.` セルサイズ [m]

[^pingel2013]: Pingel, Thomas J., Keith C. Clarke, and William A. McBride. 2013. ‘An Improved Simple Morphological Filter for the Terrain Classification of Airborne LIDAR Data’. ISPRS Journal of Photogrammetry and Remote Sensing 77 (March): 21–30. [https://doi.org/10.1016/j.isprsjprs.2012.12.002](https://doi.org/10.1016/j.isprsjprs.2012.12.002).
