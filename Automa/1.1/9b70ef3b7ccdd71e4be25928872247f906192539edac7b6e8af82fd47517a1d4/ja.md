```
compile(tokens::Vector{RE}; unambiguous=false)::TokenizerMachine
```

正規表現 `tokens` をトークナイザーマシンにコンパイルします。このマシンは `make_tokenizer` に渡すことができます。

キーワード `unambiguous` は、複数の一致するトークンのうちどれが出力されるかを決定します: `false`（デフォルト）の場合、最も長いトークンが出力されます。同じ長さのトークンが複数ある場合は、インデックスが最も高いものが返されます。`true` の場合、`make_tokenizer` は、任意の入力テキストがあいまいにトークンに分解できる場合にエラーを返します。

関連情報: [`Tokenizer`](@ref), [`make_tokenizer`](@ref), [`tokenize`](@ref)
