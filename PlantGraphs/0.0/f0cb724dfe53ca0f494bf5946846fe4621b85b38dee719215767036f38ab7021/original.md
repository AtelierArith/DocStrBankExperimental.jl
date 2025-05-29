```
rules(g::Graph)
```

Returns a tuple with all the graph-rewriting rules stored in a dynamic graph

## Examples

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> rule = Rule(A, rhs = x -> A() + B());

julia> rules_graph = Graph(axiom = axiom, rules = rule);

julia> rules(rules_graph);
```
