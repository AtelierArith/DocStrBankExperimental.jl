```
VTUHeader(::Type{T},input::Vector{UInt8}) where {T<:Union{UInt32,UInt64}}
```

ヘッダタイプとBase64デコードされた入力データ配列に基づいてVTUHeaderを計算します。

# コンストラクタ

  * `::Type{T}`: ヘッダタイプ、UInt32またはUInt64のいずれか
  * `input::Vector{UInt8}`: 入力データ

# フィールド

  * `num_blocks::T` : ブロックの数
  * `blocksize::T` : ブロックのサイズ
  * `last_blocksize::T` : 最後のブロックのサイズ（異なる場合があります）
  * `compressed_blocksizes::T` : 圧縮されたブロックのサイズ
