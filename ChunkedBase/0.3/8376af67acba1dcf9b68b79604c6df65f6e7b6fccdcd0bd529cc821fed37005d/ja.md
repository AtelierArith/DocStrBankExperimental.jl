```
populate_result_buffer!(
    result_buf::AbstractResultBuffer,
    newline_segment:AbstractVector{Int32},
    parsing_ctx::AbstractParsingContext,
    bytes::Vector{UInt8},
    comment::Union{Nothing,Vector{UInt8}}=nothing,
    ::Type{CT}=Tuple{}
) where {CT}
```

`parsing_ctx.bytes`内の改行位置`newline_segment`の間にある入力バイトを`result_buf`に解析するためのカスタムロジックを提供するために、`AbstractParsingContext`をオーバーライドします。このメソッドは、異なる`newline_segment`を持つ複数のタスクから並行して呼び出され、一部は同じ`parsing_ctx.bytes`を共有します。`result_buf`は、一度に1つのタスクによってのみアクセスされます。

# 引数:

  * `result_buf`: この関数からの解析結果を格納するために意図されたユーザー提供のオブジェクト
  * `newline_segment`: 入力の行を区切る`bytes`内の改行位置のベクター
  * `parsing_ctx`: このメソッドを呼び出し、解析特有の設定を持つために使用されるユーザー提供のオブジェクト
  * `bytes`: 入力から取り込まれた生のバイト
  * `comment`: スキップするコメントプレフィックス（ある場合）
  * `CT`: `parse_file_parallel` / `parse_file_serial`に渡されたオプションのコンパイル時に知られているオブジェクト

# 注意:

各連続する`newline_segment`の値のペアは、`bytes`内の排他的なバイト範囲を定義し、これが単一の行を構成します。

範囲は排他的に扱う必要があります。なぜなら、位置0のチャンクの先頭と、ファイルが改行で終わらない場合はファイルの終わりの後に架空の改行を追加するからです。各行を安全に処理する方法は、例えば次のようになります：

```
start_index = first(newline_segment)
for i in 2:length(newline_segment)
    end_index = newline_segment[i]
    row_bytes = view(bytes, start_index+1:end_index-1) # +/- 1が必要！

    # ... 実際にresult_bufを埋める

    start_index = end_index
end
```
