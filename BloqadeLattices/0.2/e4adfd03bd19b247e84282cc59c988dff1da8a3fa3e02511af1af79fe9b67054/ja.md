```
lattice_vectors(r::RectangularLattice)
```

長方形格子のブレーヴィス格子ベクトルを浮動小数点数を含むタプルのタプルとして返します。

ベクトルは次のように定義されます：

  * 𝐚₁ = (1.0, 0.0)
  * 𝐚₂ = (0.0, `r.aspect_ratio`)、ここで `aspect_ratio` は `Float64` です。
