BlockHaloArrayを構築する

# 引数

  * `dims::NTuple{N,Int}`: 配列の次元
  * `nhalo::Integer`: ハロエントリの数（すべての次元で等しい）

# キーワード引数

  * `nblocks::Integer`: 配列を分割するブロックの数; デフォルトはnthreads()
  * `T`:: 配列の数値型; デフォルトはFloat64
