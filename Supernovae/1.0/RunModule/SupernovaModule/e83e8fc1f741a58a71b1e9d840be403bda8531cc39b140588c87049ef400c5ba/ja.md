```
Supernova(data::Dict{String,Any}, config::Dict{String,Any})
```

`data`からスーパーノヴァをロードします。`data`にはスーパーノヴァデータとオプションを含むいくつかのキーがあります。

  * `NAME::String`: スーパーノヴァの名前
  * `ZEROPOINT::Float64`: スーパーノヴァのゼロポイント
  * `ZEROPOINT_UNIT::String`: ゼロポイントの単位、デフォルトはAB_mag
  * `REDSHIFT::Float64`: スーパーノヴァの赤方偏移
  * `MAX_FLUX_ERR::Float64`: 許可される最大フラックス誤差、デフォルトはinf
  * `MAX_FLUX_ERR_UNIT::String`: 最大フラックス誤差の単位
  * `PEAK_TIME::Union{Bool, Float64}`: boolの場合、ピークフラックスに対する時間を設定するかどうか、Float64の場合、PEAK_TIMEに対する時間を設定
  * `OBSERVATIONS::Vector{Dict{String,Any}}`: [`Lightcurve`](@ref)に変換されるデータ
