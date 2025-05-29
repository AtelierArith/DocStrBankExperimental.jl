```
movefromstring(s::String)
```

UCIムーブ文字列をムーブに変換します。

入力文字列が有効なUCIムーブでない場合は`nothing`を返します。

# 例

```julia-repl
julia> movefromstring("d2d4") == Move(SQ_D2, SQ_D4)
true

julia> movefromstring("h7h8q") == Move(SQ_H7, SQ_H8, QUEEN)
true

julia> movefromstring("f7f9") == nothing
true

julia> movefromstring("") == nothing
true
```
