```
SplinePSF(psf::AbstractPSF, 
          x_range::AbstractRange, 
          y_range::AbstractRange;
          order::Integer=3)
```

2DのSplinePSFを作成するには、2Dグリッド上でPSFをサンプリングします（z=0で）。

# 引数

  * `psf`: サンプリングする元のPSF
  * `x_range`: マイクロメートル単位でサンプリングするx座標の範囲
  * `y_range`: マイクロメートル単位でサンプリングするy座標の範囲
  * `order`: 補間の次数（デフォルト: 3は三次）

# 戻り値

  * `SplinePSF`: サンプリングされたPSFの2Dスプライン補間

# 注意

  * 3D PSFの場合、これはz=0でのみサンプリングします
