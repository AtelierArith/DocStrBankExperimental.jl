```
surreal2dot(x::SurrealFinite)
surreal2dot(io::IO, x::SurrealFinite)
```

サーフィリアル表現を木としてDOT形式で出力し、GraphVisを使用して描画し、グラフ内のノード数を返します。

## 引数

  * `io::IO`: 出力ストリーム、デフォルトはstdout
  * `x::SurrealFinite`: 出力する数

## 例

```jldoctest
julia> surreal2dot(convert(SurrealFinite, 1))
digraph "1.0" {
   node_1 [shape=none,margin=0,label=
         <<TABLE BORDER="0" CELLBORDER="1" CELLSPACING="0" CELLPADDING="4">
         <TR><TD COLSPAN="2">1</TD></TR>
         <TR><TD PORT="L"> <TABLE BORDER="0" CELLBORDER="0" CELLPADDING="0"><TR><TD PORT="0,1"> 0 </TD> &nbsp; </TR></TABLE> </TD><TD PORT="R"> ϕ </TD></TR>
         </TABLE>>,
         ];
   node_1:"0,1" -> node_2;
   node_2 [shape=none,margin=0,label=<<B>0</B>>]
}
2
```
