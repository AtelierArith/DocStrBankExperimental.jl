```
filter_by_class!(library::SpectralLibrary)
```

`SpectralLibrary`内のスペクトルを`library.class_valid_keys`に基づいてフィルタリングします。

  * `library.spectra`と`library.classes`を更新して、`library.class*valid*keys`に一致するもののみを含めます。

# 注意事項

  * この関数は`library`をその場で変更します。
  * `library.class_valid_keys`が`nothing`の場合、フィルタリングが行われないことを示すメッセージをログに記録し、変更を加えずに終了します。
