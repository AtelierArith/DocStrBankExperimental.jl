```
SpectralLibrary(file_name::String,
    class_header_name::String,
    spectral_starting_column::Int64=2,
    truncate_end_columns::Int64=0,
    class_valid_keys=nothing,
    scale_factor=1.0,
    wavelength_regions_ignore=[0, 440, 1310, 1490, 1770, 2050, 2440, 2880])
```

`SpectralLibrary`構造体のコンストラクタ。

# 引数

  * `file_name::String`: エンドメンバーライブラリデータファイル名、CSVライク。
  * `class_header_name::String`: データファイル内のクラスラベルの列。
  * `spectral_starting_column::Int64=2`: スペクトルデータの開始列
  * `truncate_end_columns::Int64=0`: データの末尾から無視する列の数。
  * `class_valid_keys=nothing`: 有効なクラスラベルのリスト。
  * `scale_factor::Float64=1.0`: スペクトルスケーリングファクター。
  * `wavelength_regions_ignore=[0,440,1310,1490,1770,2050,2440,2880]`: リスト内の開始/終了ペアとして無視する波長領域のリスト。
