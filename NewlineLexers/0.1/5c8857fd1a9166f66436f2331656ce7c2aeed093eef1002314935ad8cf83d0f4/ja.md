```
find_newlines!(l::Lexer, buf::Vector{UInt8}, out::AbstractVector{Int32}, curr_pos::Int=firstindex(buf), end_pos::Int=lastindex(buf))
```

`buf[curr_pos:end_pos]`内の改行を見つけ、その位置を`out`に追加します。改行の位置は`buf`の先頭からの相対位置です。`Lexer`の型は、引用符やエスケープの処理ルールを決定します。詳細は`Lexer`を参照してください。

`end_pos`は`typemax(Int32)`未満でなければならず、`1 <= curr_pos <= end_pos`です。
