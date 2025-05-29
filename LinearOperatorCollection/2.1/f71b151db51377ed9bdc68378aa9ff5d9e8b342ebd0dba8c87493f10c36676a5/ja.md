GradientOp(T::Type; shape::Tuple, dims=1:length(shape))

配列のサイズ `shape` に沿った次元 `dims` に沿った方向勾配演算子。

# 必須引数

  * `T`                        - 要素の型、例えば `ComplexF32` の場合は `Float64`

# 必須キーワード引数

  * `shape::NTuple{N,Int}`     - 配列の形状（例：画像）

# オプションのキーワード引数

  * `dims`                     - 勾配が適用される次元；デフォルトは `1:length(shape)`
