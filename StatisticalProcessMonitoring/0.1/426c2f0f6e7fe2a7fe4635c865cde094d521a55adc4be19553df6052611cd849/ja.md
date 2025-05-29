```
StationaryBootstrap{T} <: AbstractSampling
```

定常ブロックブートストラップサンプリング法を表し、ブロックの長さは`Geometric`乱数変数からサンプリングされます。

# フィールド

  * `block::T`: 現在サンプリングされているデータのブロック。
  * `blocksize::Int`: 各ブロックの平均サイズ。
  * `t::Int`: ブロック内の現在のインデックス。

# コンストラクタ

  * `StationaryBootstrap(blocksize::Int, data::Vector{T}) where T`: データのベクトル用の`StationaryBootstrap`オブジェクトを構築します。
  * `StationaryBootstrap(blocksize::Int, data::Matrix{T}) where T`: データの行列用の`StationaryBootstrap`オブジェクトを構築します。
