```
ParsedPayload{B, C<:AbstractParsingContext}
```

解析された結果のペイロードであり、各 `populate_result_buffer!` 呼び出しの後に `consume!` に渡されます。

# フィールド:

  * `row_num::Int`: ペイロード内の最初の行の行番号
  * `len::Int`: ペイロード内の行数
  * `results::B`: `populate_result_buffer!` によって populated された解析結果バッファ
  * `parsing_ctx::C`: ライブラリ提供のデータ（JSONL と CSV 処理を区別するため）
  * `chunking_ctx::ChunkingContext`: 生のバイト、同期オブジェクト、および改行位置を含む
  * `eols_buffer_index::Int32`: このペイロードが対応する `chunking_ctx.newline_positions` 内の改行位置の開始インデックス。

# 参照:

  * [`consume!`](@ref), [`AbstractParsingContext`](@ref), [`ChunkingContext`](@ref), [`AbstractResultBuffer`](@ref), [`PayloadOrderer`](@ref)
