```
first_chunk(memory::Vector{<:Chunk}; check_value=true, criteria...)
```

メモリ内で条件に一致する最初のチャンクを返します

# 引数

  * `memory::Vector{<:Chunk}`: チャンクのベクター

# キーワード

  * `check_value=true`: スロット値をチェックする
  * `criteria...`: チャンクに一致させるためのオプションのキーワード引数
