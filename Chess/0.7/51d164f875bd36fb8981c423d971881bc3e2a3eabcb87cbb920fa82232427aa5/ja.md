```
squarefromstring(s::AbstractString)
```

文字列を `Square` に変換しようとします。

返り値の型は `Union{Square, Nothing}` です。

入力文字列が短すぎる場合、または最初の2文字が標準代数表記で正方形を表さない場合、`nothing` を返します。最初の2文字が有効な正方形を表す場合、その正方形が返されます。追加の文字があっても問題ありません。

# 例

```julia-repl
julia> squarefromstring("d6")
SQ_D6

julia> squarefromstring("xy") == nothing
true

julia> squarefromstring("") == nothing
true

julia> squarefromstring("g1f3")
SQ_G1
```
