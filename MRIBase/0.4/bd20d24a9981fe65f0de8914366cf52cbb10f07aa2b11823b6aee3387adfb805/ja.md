```
EPITrajectory(T, numProfiles, numSamplingPerProfile
              ; TE::T=0.0
              , AQ::T=1.e-3
              , EPI_factor::Int64=1
              , profileOffset= :equispaced
              , kargs...)
```

は2次元のカーテシアン軌道を返します。

# 引数

  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`TE::T=0.0`)             - エコー時間（秒）
  * (`AQ::T=1.e-3`)           - 読出し時間（秒）（プロファイルごと）
  * (`EPI_factor::Int64=1`)         - EPIファクター、例えば、ショットごとに取得するプロファイルの数
  * (`profileOffset= :equispaced`)  - 等間隔またはランダムなショットの順序
