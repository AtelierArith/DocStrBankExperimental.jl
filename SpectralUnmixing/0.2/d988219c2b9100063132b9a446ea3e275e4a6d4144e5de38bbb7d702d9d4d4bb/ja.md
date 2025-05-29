```
remove_wavelength_region_inplace!(library::SpectralLibrary, set_as_nans::Bool=false)
```

`library.good_bands`の外側にある波長領域を、NaNに設定するか、フィルタリングすることによって`library`から削除します。

# 注意事項

  * この関数は`library`をその場で変更します。
