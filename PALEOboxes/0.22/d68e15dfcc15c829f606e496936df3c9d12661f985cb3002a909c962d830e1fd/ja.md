```
doc_reaction(class::AbstractString)
```

[`find_reaction`](@ref)を使用して「class」を調べ、Julia REPLで完全修飾の反応タイプとドキュメント文字列を表示します。

注: VS Codeのドキュメントブラウザには同様の機能があり、使用するのが簡単なことがよくあります。主な違いは、VS Codeプロジェクトおよびエディタウィンドウで*可視の定義*を見ているのに対し、`doc_reaction`は現在REPLで*利用可能な定義*、つまり現在REPLにロードされているモジュールによって提供される定義を見ていることです。
