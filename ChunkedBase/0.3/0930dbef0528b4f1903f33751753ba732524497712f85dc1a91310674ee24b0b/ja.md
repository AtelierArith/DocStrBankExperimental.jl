```
ChunkingContext(
    buffersize::Integer,
    nworkers::Integer,
    limit::Integer,
    comment::Union{Nothing,UInt8,String,Char,Vector{UInt8}}
) -> ChunkingContext
```

単一のファイルをチャンクごとに並列解析するための調整オブジェクトです。

ユーザーはこのオブジェクトを使用して、割り当てるバイトバッファのサイズ、生成するワーカータスクの数、および`parse_file_parallel`で解析する最大行数を指定できます。

# 引数:

  * `buffersize`: 割り当てるバイトバッファのサイズ。入力が`buffersize`より大きい場合、二次の`ChunkingContext`オブジェクトが使用され、`buffersize`と同じサイズの新しいバッファが割り当てられます。
  * `nworkers`: `parse_file_parallel`で生成すべきワーカータスクの数。
  * `limit`: 解析する最大行数。`limit_eols!`を参照してください。デフォルトでは制限は設定されていません。
  * `comment`: スキップするコメントプレフィックス（ある場合）。デフォルトではコメントプレフィックスはスキップされません。

# 注意:

  * `id`および`buffer_refills`フィールドを使用して、入力のチャンクを一意に識別できます。

`id`フィールドは、内部で二次の`ChunkingContext`オブジェクトを作成するために必要であり、その`id`は元の`ChunkingContext`の`id` + 1に等しくなります。

  * `counter`フィールドは、パーサー/コンシューマタスクを同期させるために使用されます。
  * `newline_positions`フィールドは、入力内の改行位置を格納するために使用されます。
  * `bytes`フィールドは、入力から取り込まれた生のバイトを格納するために使用されます。
  * `comment`は、`skip_rows_init!`で*初期*のコメント行をスキップするために使用できます。この値は、解析中にファイルの中間でコメント行を処理するために`populate_result_buffer!`に渡されます（`_startswith`を使用してチェックを行うことができます）。
  * `buffersize`は、入力内の最長行を収容できる十分な大きさである必要があります。そうでないと、レキサーは失敗します。
  * `buffersize`は、各`nworkers`タスクが作業するのに十分なバイトを持つように選択する必要があります。タスクごとに1MiBを使用することは、実際には合理的にうまく機能するようです。

# 参照:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref)
