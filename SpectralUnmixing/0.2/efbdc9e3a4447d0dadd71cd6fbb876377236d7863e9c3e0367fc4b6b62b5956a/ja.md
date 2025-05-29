```
interpolate_library_to_new_wavelengths!(library::SpectralLibrary, new_wavelengths::Array
{Float64})
```

`library`のスペクトルを新しい波長に補間します。

  * 線形補間を行い、平坦な外挿境界条件を適用します。
  * `library.wavelengths`、`library.good_bands`、および`library.spectra`行列を再サンプリングされたスペクトルに更新します。

# 注意事項

  * この関数は`library`をその場で変更します。
