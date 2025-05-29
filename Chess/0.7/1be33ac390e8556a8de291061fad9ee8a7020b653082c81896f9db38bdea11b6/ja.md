```
movefromsan(b::Board, san::String, movelist::MoveList)::Union{Move,Nothing}
movefromsan(b::Board, san::String)::Union{Move,Nothing}
```

短縮代数記法での手を読み取ろうとします。

提供された文字列が不可能または曖昧な手である場合、`nothing`を返します。

これは内部的に`moves`を呼び出し、不要なアロケーションによる時間/スペースの節約のために事前に割り当てられた`MoveList`を供給することができます。提供された場合、`movelist`パラメータは`moves`に渡されます。`movelist`が十分な容量を持っていることを確認するのは呼び出し元の責任です。

# 例

```julia-repl
julia> movefromsan(b, "Nf3")
Move(g1f3)

julia> movelist = MoveList(200)
0-element MoveList

julia> movefromsan(b, "Nf3", movelist)
Move(g1f3)

julia> movefromsan(b, "???") == nothing
true
```
