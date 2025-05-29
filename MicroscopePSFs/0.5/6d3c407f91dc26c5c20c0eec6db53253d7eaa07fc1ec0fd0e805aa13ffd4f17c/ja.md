```
save_psf(filename::String, object; metadata::Dict=Dict())
```

PSFまたは関連オブジェクト（例：ZernikeCoefficients、PupilFunction）をHDF5ファイルに保存します。

# 引数

  * `filename`: PSFが保存されるパス
  * `object`: 保存するオブジェクト（PSF、ZernikeCoefficients、PupilFunctionなど）
  * `metadata`: 含める追加メタデータのオプション辞書

# 戻り値

  * チェイニングのための`filename`
