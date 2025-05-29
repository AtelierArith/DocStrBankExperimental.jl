```
CartesianTrajectory(T, numProfiles, numSamplingPerProfile
              ; TE::T=0.0
              , AQ::T=1.e-3
              , kmin=(-0.5,-0.5)
              , kmax=(0.5,0.5)
              , kargs...)
```

は2次元のカーテシアン軌道を返します。

# 引数

  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`TE::Float64=0.0`)             - エコー時間（秒）
  * (`AQ::Float64=1.e-3`)           - 読出し時間（秒）（プロファイルごと）
  * (`kmin=(-0.5,-0.5)`)            - カバーされるk空間の最小値（部分フーリエイメージング用）
  * (`kmax=(-0.5,-0.5)`)            - カバーされるk空間の最大値（部分フーリエイメージング用）
