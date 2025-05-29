```
load_psf(filename::String)
```

HDF5ファイルからPSFまたは関連オブジェクト（例：ZernikeCoefficients、PupilFunction）をロードします。

# 引数

  * `filename`: 保存されたPSFオブジェクトを含むHDF5ファイルへのパス

# 戻り値

  * 元のタイプ（PSF、ZernikeCoefficients、PupilFunctionなど）のオブジェクト

# 例

```julia
# 以前に保存されたPSFをロード
psf = load_psf("my_airy_psf.h5")

# 通常通りにロードしたPSFを使用
intensity = psf(0.1, 0.2)

# Zernike係数をロードして使用
zc = load_psf("zernike_coeffs.h5")
psf = ScalarPSF(1.4, 0.532, 1.518; zernike_coeffs=zc)
```

参照: [`save_psf`](@ref)
