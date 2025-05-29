```
apply(g::Graph, query::Query)
```

Return an array with all the nodes in the graph that match the query supplied by the user.

# Examples

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> g = Graph(axiom = axiom);

julia> query = Query(A);

julia> apply(g, query);
```
