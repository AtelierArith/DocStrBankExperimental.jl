```
(psf::ScalarPSF)(x::Real, y::Real, z::Real)
```

与えられた3D位置でのPSF強度を評価します。

# 引数

  * `x, y, z`: PSF中心に対するマイクロメートル単位の位置

# 戻り値

  * 指定された位置での強度値

# 注意事項

  * 複素場の|amplitude|²として計算されます
  * 標準の演算子構文に従います: `intensity = psf(x, y, z)`
