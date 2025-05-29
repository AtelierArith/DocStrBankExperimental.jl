```
KooshballTrajectory(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , kargs...)
```

3Dのクーシュボールの軌道を返します。

# 引数

  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`TE::Float64=0.0`)             - エコー時間（秒）
  * (`AQ::Float64=1.e-3`)           - 読み出し時間（秒）（プロファイルごと）
