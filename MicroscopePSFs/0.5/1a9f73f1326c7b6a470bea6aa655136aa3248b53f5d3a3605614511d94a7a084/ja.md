```
amplitude(psf::SplinePSF, x::Real, y::Real, z::Real)
```

位置 (x, y, z) における 3D PSF の複素振幅を計算します。

# 引数

  * `psf`: SplinePSF インスタンス
  * `x, y, z`: PSF 中心に対するマイクロメートル単位の座標

# 戻り値

  * 複素振幅 = sqrt(intensity) で位相はゼロ

# 注意事項

  * 他の PSF のインターフェースに合わせるために sqrt(intensity) を複素数として返します
  * SplinePSF は位相情報をモデル化していません
