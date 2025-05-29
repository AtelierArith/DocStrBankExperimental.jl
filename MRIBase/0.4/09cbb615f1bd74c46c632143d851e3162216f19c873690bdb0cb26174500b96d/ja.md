```
trajectory(trajName::AbstractString, numProfiles::Int, numSamplingPerProfile::Int; numSlices::Int64=1, TE::Float64=0.0, AQ::Float64=1.e-3, kargs...)
```

は、その `name` から軌道を構築するためのファクトリメソッドです。

# 引数

  * `name::String`                  - 軌道の名前
  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`numSlices::Int64=1`)          - スライスの数（3D軌道用）
  * (`TE::Float64=0.0`)             - エコー時間（秒）
  * (`AQ::Float64=1.e-3`)           - 読出し時間（秒）（プロファイルごと）
  * `kargs...`                      - 追加のキーワード引数
