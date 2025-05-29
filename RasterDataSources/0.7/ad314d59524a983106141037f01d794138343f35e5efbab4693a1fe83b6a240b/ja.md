```
getraster(source::Type{<:ALWB{Union{Deciles,Values},Union{Day,Month,Year}}}, [layer]; date)
```

[`ALWB`](@ref) 気象データを [www.bom.gov.au/water/landscape](http://www.bom.gov.au/water/landscape) から値またはデシルとして、`Day`、`Month`、または `Year` の時間ステップでダウンロードします。

# 引数

  * `layer`: `Symbol` または `(:rain_day, :s0_pct, :ss_pct, :sd_pct, :sm_pct, :qtot, :etot, :e0, :ma_wet, :pen_pet, :fao_pet, :asce_pet, :msl_wet, :dd)` の `Symbol` のタプル。`layer` 引数がない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

# キーワード

  * `date`: `DateTime`、`AbstractVector` の `DateTime` または開始日と終了日のタプル。複数の日付の場合、複数のファイル名の `Vector` が返されます。ALWB は日次、月次、年次の時間ステップで利用可能です。

# 例

これは、あなたの日付を含む年平均を含むファイルを返します：

```julia
julia> getraster(ALWB{Values,Year}, :ss_pct; date=Date(2001, 2))
"/your/RASTERDATASOURCES_PATH/ALWB/values/month/ss_pct.nc"
```

ダウンロードされたファイルまたは既存のファイルのファイルパスが返されます。
