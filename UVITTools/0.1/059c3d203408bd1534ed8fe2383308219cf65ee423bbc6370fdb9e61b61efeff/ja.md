`write_uvit_grating_phafile(uvit_detector, uvit_grating, channels, counts, exptime_sec[, phafile="phafile.pha"])`

グレーティングカウントスペクトルからOGIP互換のPHAスペクトルファイルを作成します - チャンネル対カウント。

この関数は、グレーティング分光ツールによって使用されます。 ...

# 引数

  * `uvit_detector::String`: FUVまたはNUV。
  * `uvit_grating::String`: UVITグレーティングのいずれか - FUV-Grating1、FUV-Grating2、NUV-Grating。
  * `channels::Array{Int64}`: スペクトルチャンネルの配列。
  * `counts::Array{Float64}`: スペクトルチャンネル配列に対応するカウントの配列。
  * `exposure_time_sec::Float64`: 露光時間（秒）。

# オプション

  * `phafile::String`: 生成されるPHAスペクトルファイルの名前。

...
