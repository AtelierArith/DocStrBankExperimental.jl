```
parse_file_parallel(
    lexer::Lexer,
    parsing_ctx::AbstractParsingContext,
    consume_ctx::AbstractConsumeContext,
    chunking_ctx::ChunkingContext,
    result_buffers::Vector{<:AbstractResultBuffer},
    ::Type{CT}=Tuple{}
) where {CT} -> Nothing
```

`lexer.io`内のファイルを`chunking_ctx.nworkers`タスクを使用して並列に解析します。ユーザーは、`chunking_ctx.bytes`内の取り込まれたデータを解析するために使用される`populate_result_buffer!`メソッドを提供する必要があります。`chunking_ctx.newline_positions`内の改行位置を`result_buffers`への行境界として使用します。各`populate_result_buffer!`呼び出しの後に`consume!`メソッドが呼び出されるため、ユーザーは並列に解析された結果を処理できます。`result_buffer`は、一度に1つのタスクによってのみアクセスされます。

# 引数:

  * `lexer`: 入力内の改行位置を見つけるために使用される`NewlineLexers.Lexer`オブジェクト。レキサーのタイプは、検索が引用符を意識するかどうかに影響します。
  * `parsing_ctx`: `populate_result_buffer!`に渡されるユーザー提供のオブジェクト
  * `consume_ctx`: `consume!`に渡されるユーザー提供のオブジェクト
  * `chunking_ctx`: 現在処理中のデータのチャンクを追跡するために使用される内部オブジェクト
  * `result_buffers`: 解析された結果を格納するために使用されるユーザー提供のオブジェクトのベクター
  * `CT`: `populate_result_buffer!`に渡されるオプションのコンパイル時に知られている型。

これは、ChunkedCSVによって必要とされるニッチな機能であり、解析ループを展開するためにコンパイル時に「カスタム型」について知っている必要があります。

# 例外:

  * `UnmatchedQuoteError`: 入力が一致しない引用符で終了する場合
  * `NoValidRowsInBufferError`: 入力バッファ内に改行が見つからなかった場合
  * `CapturedException`: パーサー/コンシューマータスクの1つで例外がスローされた場合

# 注意:

  * `read_and_lex!`を使用して自分で`chunking_ctx`を初期化するか、`initial_read!` + `initial_lex!`を使用して、`parse_file_parallel`を呼び出す前に最初のデータチャンクをスニッフする機会を得ることができます。
  * 入力が`chunking_ctx.bytes`より大きい場合、二次の`chunking_ctx`オブジェクトが使用され、入力をダブルバッファリングします。これにより、`chunking_ctx.bytes`と同じサイズの新しいバッファが割り当てられます。
  * この関数は`chunking_ctx.nworkers` + 1タスクを生成します。

[`populate_result_buffer!`](@ref)、[`consume!`](@ref)、[`parse_file_serial`](@ref)も参照してください。
