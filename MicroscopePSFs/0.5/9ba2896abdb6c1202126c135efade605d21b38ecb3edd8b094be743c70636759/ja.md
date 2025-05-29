```
amplitude(psf::SplinePSF, x::Real, y::Real)
```

位置 (x, y) での PSF の複素振幅を z=0 で計算します。

# 引数

  * `psf`: SplinePSF インスタンス
  * `x, y`: PSF 中心に対するマイクロメートル単位の座標

# 戻り値

  * 複素振幅 = sqrt(intensity) で位相はゼロ
