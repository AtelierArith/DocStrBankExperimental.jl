```
surreal2dag(x::SurrealFinite)
surreal2dag(io::IO, x::SurrealFinite)
```

サラリウム表現をDAGとしてDOT形式で出力し、GraphVisを使用して描画し、グラフ内のノード数を返します。グラフ内のノード数を返します。

## 引数

  * `io::IO`: 出力ストリーム、デフォルトはstdout
  * `x::SurrealFinite`: 出力する数

## 例

```jldoctest
julia> surreal2dag(convert(SurrealFinite, 0))
digraph "0.0" {
   node_1 [shape=none,margin=0,label=
         <<TABLE BORDER="0" CELLBORDER="1" CELLSPACING="0" CELLPADDING="4">
         <TR><TD COLSPAN="2">0</TD></TR>
         <TR><TD PORT="L"> ∅ </TD><TD PORT="R"> ∅ </TD></TR>
         </TABLE>>,
         ]; 
}
1
```
