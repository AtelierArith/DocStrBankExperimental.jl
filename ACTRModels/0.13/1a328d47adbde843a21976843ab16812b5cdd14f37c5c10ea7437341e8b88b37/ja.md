```
get_chunks(memory::Vector{<:AbstractChunk}; check_value=true, criteria...)
```

指定された基準に一致するすべてのチャンクを返します。

# 引数

  * `memory::Vector{<:AbstractChunk}`: チャンクオブジェクトのベクター

# キーワード

  * `check_value=true`: スロット値をチェックする

-`criteria...`: チャンクの一致に対応するオプションのキーワード引数
