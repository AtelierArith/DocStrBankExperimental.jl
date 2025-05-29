```
get_tool_citation(io::IO=stdout; jl = true, texttt = false, copy = true, cite_commands=Dict{String,String}(), filename="julia_citations.bib", badge=false)
```

現在の環境で使用されているパッケージを説明する文を印刷します。直接の依存関係のみを考慮したい場合は、`only_direct=true`を設定できます。この文は自動的にクリップボードにコピーされます（`copy=false`を使用することでこれを避けることができます）。パッケージ名はデフォルトで.jlの拡張子が付いています。`jl=false`を使用することでこれを省略できます。パッケージ名は、`texttt=true`を設定することで`texttt`で囲むことができ、各パッケージに使用する引用コマンドを`cite_commands=Dict("PackageName"=>"custom_cite")`を使用してカスタマイズすることもできます。.bibファイルのファイル名は、`filename`キーワードを介して渡すことができます。`badge = true`を使用すると、`Citation.bib`ファイルがないがDOIバッジがあるパッケージから引用を取得できます。
