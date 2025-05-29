```
load_data!(library::SpectralLibrary)
```

`SpectralLibrary`オブジェクトに関連するスペクトルデータをロードして前処理します。

  * CSVライクなファイル`library.file_name`からスペクトルデータをロードします。
  * 波長無視領域をペアセット`library.wavelength_regions_ignore`に処理します。
  * `library.spectra`、`library.classes`、および`library.class_valid_keys`をロードします。
  * `library.wavelengths`をナノメートルとしてソートしてロードし、それに応じてスペクトルデータを再配置します。
  * `library.wavelength_regions_ignore`に基づいてマスク`library.good_bands`を生成します。

# 戻り値

  * ロードされ処理されたデータを持つ更新された`SpectralLibrary`インスタンス。
