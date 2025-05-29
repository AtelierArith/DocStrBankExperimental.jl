```
amplitude(psf::AbstractPSF, x::Real, y::Real)
```

PSF中心に対する位置(x,y)での複素場振幅を評価します。

# 引数

  * `x, y`: PSF中心に対する位置（マイクロメートル単位）

# 戻り値

  * |amplitude|²が正規化された強度を与えるように正規化された複素振幅

# 座標

入力座標(x,y)はPSF中心に対する物理単位（マイクロメートル）です。

# 例

```julia
psf = AiryPSF(1.4, 0.532)
amp = amplitude(psf, 0.1, 0.2)
intensity = abs2(amp)  # 強度に変換
```
