ParticleTrackerは、粒子のアドベクションからの軌跡を出力するためのコールバックとして実装されています。次のように追加します。

```
add!(model.callbacks, ParticleTracker(spectral_grid; kwargs...))
```

出力はnetCDFを介して行われます。フィールドとオプションは次のとおりです。

  * `schedule::SpeedyWeather.Schedule`: [OPTION] 粒子追跡をスケジュールするタイミング
  * `file_name::String`: [OPTION] netCDFファイルのファイル名
  * `compression_level::Int64`: [OPTION] ロスレス圧縮レベル; 1=低速だが速い、9=高速だが遅い
  * `shuffle::Bool`: [OPTION] 圧縮のためのシャッフル/ビットトランスポーズフィルター
  * `keepbits::Int64`: [OPTION] 保持する仮数ビット、(14, 15, 16)は少なくとも(2km, 1km, 500m)の精度の位置を意味します
  * `nparticles::Int64`: 追跡する粒子の数
  * `netcdf_file::Union{Nothing, NCDatasets.NCDataset}`: 書き込むnetcdfファイル、初期化時に作成されます
  * `lon::Vector`
  * `lat::Vector`
  * `σ::Vector`
