```
see(b::Board, m::Move)::Int
see(b::Board, m::String)::Int
see(b::Board, m::String, movelist::MoveList)::Int
```

静的交換評価器。

この関数は、移動の材料の獲得/損失を推定します。検索を行うことなく、目的のマスの攻撃者と防御者を見て、X線攻撃者と防御者を含みます。ピン、過負荷の駒などは考慮されないため、非常に粗い推測としてのみ信頼できます。

`m::String`内で、`see`は内部的に`movesfromsan`を呼び出します。これは、不要な割り当てによる時間/スペースの節約のために、事前に割り当てられた`MoveList`を供給することができます。提供された場合、`movelist`パラメータは`moves`に渡されます。`movelist`が十分な容量を持っていることを確認するのは呼び出し元の責任です。

# 例

```julia-repl
julia> b = fromfen("8/4k3/8/4p3/8/2BK4/8/q7 w - - 0 1")
Board (8/4k3/8/4p3/8/2BK4/8/q7 w - -):
 -  -  -  -  -  -  -  -
 -  -  -  -  k  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  p  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  -  -  -
 -  -  -  -  -  -  -  -
 q  -  -  -  -  -  -  -

julia> see(b, "Bxe5")
-2

julia> b = fromfen("7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - - 0 1")
Board (7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - -):
 -  -  -  -  -  -  -  q
 -  -  -  -  k  -  b  -
 -  -  -  p  -  -  -  -
 -  -  -  -  n  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  N  -  -
 -  -  -  -  R  -  -  -
 -  -  -  -  R  -  -  -

julia> see(b, "Nxe5")
1

julia> b = fromfen("7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - - 0 1")
Board (7q/4k1b1/3p4/4n3/8/2BK1N2/4R3/4R3 w - -):
 -  -  -  -  -  -  -  q
 -  -  -  -  k  -  b  -
 -  -  -  p  -  -  -  -
 -  -  -  -  n  -  -  -
 -  -  -  -  -  -  -  -
 -  -  B  K  -  N  -  -
 -  -  -  -  R  -  -  -
 -  -  -  -  R  -  -  -

julia> movelist = MoveList(200)
0-element MoveList

julia> see(b, "Nxe5", movelist)
1
```
