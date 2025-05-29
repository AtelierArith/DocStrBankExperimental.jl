data(g::Graph)

Returns the graph-level variables.

## Example

```jldoctest
julia> struct A <: Node end;

julia> axiom = A();

julia> g = Graph(axiom = axiom, data = 2);

julia> data(g);
```
