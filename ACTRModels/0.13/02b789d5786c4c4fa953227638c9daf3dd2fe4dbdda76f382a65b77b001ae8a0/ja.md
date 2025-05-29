```
get_chunks(memory::Vector{<:AbstractChunk}, funs...; check_value=true, criteria...)
```

指定された `criteria` に一致するすべてのチャンクを返します。これらは `funs` のリストに従って評価されます。

# 引数

  * `memory::Vector{<:AbstractChunk}`: チャンクオブジェクトのベクター
  * `funs...`: 関数のリスト

# キーワード

  * `check_value=true`: スロット値をチェックする
  * `criteria...`: チャンクの一致に対応するオプションのキーワード引数
