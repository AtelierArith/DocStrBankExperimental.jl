```
rewrite!(g::Graph)
```

Apply the graph-rewriting rules stored in the graph.

## Arguments

  * `g::Graph`: The graph to be rewritten. It will be modified in-place.

## Details

This function will match the left-hand sides of all the rules in a graph. If any node is matched by more than one rule this will result in an error. The rules are then applied in order to replaced the matched nodes with the result of executing the right hand side of the rules. The rules are applied in the order in which they are stored in the graph but the order in which the nodes are processed is not defined. Since graph rewriting is semantically a parallel process, the rules should not be rely on any particular order for their functioning.

## Returns

This function returns `nothing`, but the graph passed as input will be modified by the execution of the rules.

# Examples

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> rule = Rule(A, rhs = x -> A() + B());

julia> g = Graph(axiom = axiom, rules = rule);

julia> rewrite!(g);
```
