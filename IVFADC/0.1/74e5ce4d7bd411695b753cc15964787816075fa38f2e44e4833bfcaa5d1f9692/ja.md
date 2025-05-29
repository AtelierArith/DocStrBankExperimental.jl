```
IVFADCIndex(data [;kwargs])
```

ビリオンスケールのANN検索のための逆ファイルシステムを構築するためのメインコンストラクタ。

# 引数

  * `Matrix{T<:AbstractFloat}` 入力データ

# キーワード引数

  * `kc::Int=DEFAULT_COARSE_K` 粗い量子化ステップで使用するクラスタ数（ボロノイセル）
  * `k::Int=DEFAULT_QUANTIZATION_K` 使用する残差量子化レベルの数
  * `m::Int=DEFAULT_QUANTIZATION_M` 使用する残差量子化器の数
  * `coarse_quantizer::Symbol=DEFAULT_COARSE_QUANTIZER` 粗い量子化器
  * `coarse_distance=DEFAULT_COARSE_DISTANCE` 粗い量子化距離
  * `quantization_distance=DEFAULT_QUANTIZATION_DISTANCE` 残差量子化距離
  * `quantization_method=DEFAULT_QUANTIZATION_METHOD` 残差量子化方法
  * `coarse_maxiter=DEFAULT_COARSE_MAXITER` 粗いベクトルを取得するためのクラスタリング反復の数
  * `quantization_maxiter=DEFAULT_QUANTIZATION_MAXITER` 残差量子化のためのクラスタリング反復の数
  * `index_type=UInt32` 逆リスト内のベクトルのインデックスの型
