```
BlockBootstrap{T} <: AbstractSampling
```

(円形)ブロックブートストラップサンプリング手法を表します。

# フィールド

  * `block::T`: 現在サンプリングされているデータのブロック。
  * `blocksize::Int`: 各ブロックのサイズ。
  * `t::Int`: ブロック内の現在のインデックス。

# コンストラクタ

  * `BlockBootstrap(blocksize::Int, data::Vector{T}) where T`: データのベクトル用の`BlockBootstrap`オブジェクトを構築します。
  * `BlockBootstrap(blocksize::Int, data::Matrix{T}) where T`: データの行列用の`BlockBootstrap`オブジェクトを構築します。
