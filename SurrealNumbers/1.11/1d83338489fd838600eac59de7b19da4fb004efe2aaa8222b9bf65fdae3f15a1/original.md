```
surreal2dot(x::SurrealFinite)
surreal2dot(io::IO, x::SurrealFinite)
```

Writes a surreal representation as a tree out in DOT format for drawing using GraphVis,  and returns the number of nodes in the graph.

## Arguments

  * `io::IO`: output stream, default is stdout
  * `x::SurrealFinite`: the number to write out

## Examples

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
