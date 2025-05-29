```
image = pssm(A; exaggeration=2.3, resolution=1.0)
```

*Pingel, Clarke. 2014*による知覚的陰影傾斜マップ [^pingel2014]。

# 出力

  * `image::Gray{T,2}` グレースケール画像

# 引数

  * `A::Array{Real,2}` 入力配列
  * `exaggeration::Real=2.3` 標高を誇張するための係数
  * `cellsize::Real=1.0` 垂直解像度と異なる場合の水平解像度を考慮するためのセルのサイズ

[^pingel2014]: Pingel, Thomas, and Clarke, Keith. 2014. ‘Perceptually Shaded Slope Maps for the Visualization of Digital Surface Models’. Cartographica: The International Journal for Geographic Information and Geovisualization 49 (4): 225–40. [https://doi.org/10/ggnthv](https://doi.org/10/ggnthv).
