```
SpiralTrajectoryVarDens(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , windings::Real= 6.25
              , alpha=2.0
              , angleOffset= :equispaced
              , kargs...)
```

は、可変密度の2次元スパイラルトラジェクトリを返します。

# 引数

  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * (`TE::Float64=0.0`)             - エコー時間（秒）
  * (`AQ::Float64=1.e-3`)           - 読出し時間（秒）（プロファイルごと）
  * (`windings::Real= 6.25`)        - スパイラルプロファイルの巻数
  * (`alpha=2.0`)                   - プロファイルに沿ったサンプリングポイントの大きさの進化を説明する指数
  * (`angleOffset= :equispaced`)    - プロファイル角の間隔（`:equispaced`サンプリング、`:golden`角サンプリング、または`:random`サンプリング）
