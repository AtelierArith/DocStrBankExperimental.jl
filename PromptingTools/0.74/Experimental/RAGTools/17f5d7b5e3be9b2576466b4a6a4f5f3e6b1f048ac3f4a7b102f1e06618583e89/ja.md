```
PT.pprint(
    io::IO, r::AbstractRAGResult; add_context::Bool = false,
    text_width::Int = displaysize(io)[2], annotater_kwargs...)
```

RAG結果`r`を指定された`io`ストリームに整形して表示します。

`add_context`が`true`の場合、コンテキストも表示されます。`text_width`パラメータは出力の幅を制御するために使用できます。

追加のキーワード引数をアノテーターに提供することができます。例えば、`add_sources`、`add_scores`、`min_score`などです。詳細については`annotate_support`を参照してください。
