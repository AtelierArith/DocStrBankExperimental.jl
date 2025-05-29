```
SpiralTrajectory(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , windings::Real= 6.25
              , angleOffset= :equispaced
              , kargs...)
```

は2次元のスパイラルトラジェクトリを返します。

# 引数

  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`TE::Float64=0.0`)             - エコー時間（秒）
  * (`AQ::Float64=1.e-3`)           - 読出し時間（秒）（プロファイルごと）
  * (`windings::Real= 6.25`)        - スパイラルプロファイルの巻数
  * (`angleOffset= :equispaced`)    - プロファイル角の間隔（`:equispaced` サンプリング、`:golden` 角サンプリング、または `:random` サンプリング）
