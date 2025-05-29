```
surreal2dag(x::SurrealFinite)
surreal2dag(io::IO, x::SurrealFinite)
```

Writes a surreal representation as a DAG out in DOT format for drawing using GraphVis,  and returns the number of nodes in the graph. Returns the number of nodes in the graph. 

## Arguments

  * `io::IO`: output stream, default is stdout
  * `x::SurrealFinite`: the number to write out

## Examples

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
