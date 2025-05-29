```
brightness_normalize!(library::SpectralLibrary)
```

`library.spectra`を`library.good_bands`のRMS明るさに基づいて正規化します。

# 注意事項

  * この関数は`library`をその場で変更します。
  * 明るさの計算には`library.good_bands`のみを考慮します。
