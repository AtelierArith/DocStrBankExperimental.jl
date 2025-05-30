```
avert_emissions_profiles(; avert_region_abbr::String="", latitude::Real, longitude::Real, time_steps_per_hour::Int=1, load_year::Int=2017, avert_data_year::Int=2023)
```

この関数は、AVERTデータセットからCO2、NOx、SO2、およびPM2.5のグリッド排出率プロファイル（1年間の時系列）を取得します。もしavert*region*abbrが指定されている場合、これは緯度と経度を使用して選択されるデフォルトの地域を上書きします。返される排出プロファイルは、load_yearとの曜日の整合性に合わせて調整されます。

この関数は、REopt APIの/emissions_profileエンドポイントで使用され、特にREoptを実行する前にグリッド排出デフォルトを表示するためのウェブツールに使用されますが、REoptを実行せずにAVERTデータにアクセスする一般的な外部手段でもあります。
