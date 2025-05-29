```
unicodesymbol2string(us::Char)
```

入力文字に対するASCII表現（UnicodeシンボルのLaTeX名）を返します。入力文字がすでにASCIIであるか、`REPL.REPLCompletions.latex_symbols`にリストされていない場合、入力文字列が返されます。

```julia-repl
julia> unicodesymbol2string("β")
"beta"
julia> unicodesymbol2string("b")
"b"
```
