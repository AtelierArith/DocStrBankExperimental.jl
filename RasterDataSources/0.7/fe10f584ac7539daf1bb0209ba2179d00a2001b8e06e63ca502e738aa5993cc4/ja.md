```
ALWB{Union{Deciles,Values},Union{Day,Month,Year}} <: RasterDataSource
```

オーストラリアの景観水バランス（ALWB）データソースからのデータです。

参照: [www.bom.gov.au/water/landscape](http://www.bom.gov.au/water/landscape)

データセットにはNetCDFファイルが含まれています。これらは時間次元を持ち、各ファイルに複数の日付が保存されています。

利用可能なレイヤーは `(:rain_day, :s0_pct, :ss_pct, :sd_pct, :sm_pct, :qtot, :etot, :e0, :ma_wet, :pen_pet, :fao_pet, :asce_pet, :msl_wet, :dd)` で、日次、月次、年次の解像度で利用可能であり、`Values` または相対的な `Deciles` として提供されます。

`ALWB` の `getraster` は、ダウンロードする日付を指定するために `date` キーワードを使用する必要があります。

実装の詳細については [`getraster`](@ref) ドキュメントを参照してください。
