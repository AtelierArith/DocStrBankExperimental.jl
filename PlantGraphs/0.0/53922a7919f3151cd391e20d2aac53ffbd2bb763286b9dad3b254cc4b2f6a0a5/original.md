```
Graph(;axiom, rules = nothing, data = nothing)
```

Create a dynamic graph from an axiom, one or more rules and, optionally, graph-level variables.

## Arguments

  * `axiom`: A single object inheriting from `Node` or a subgraph generated  with the graph construction DSL. It should represent the initial state of the dynamic graph.

## Keywords

  * `rules`:  A single `Rule` object or a tuple of `Rule` objects (optional). It should include all graph-rewriting rules of the graph.
  * `data`: A single object of any user-defined type (optional). This will be the graph-level variable accessible from any rule or query applied to the graph.
  * `FT`: Floating-point precision to be used when generating the 3D geometry associated to a graph.

## Details

All arguments are assigned by keyword. The axiom and rules are deep-copied when creating the graph but the graph-level variables (if a copy is needed due to mutability, the user needs to care of that).

## Returns

An object of type `Graph` representing a dynamic graph. Printing this object results in a human-readable description of the type of data stored in the graph.

## Examples

```jldoctest
julia> struct A0 <: Node end;

julia> struct B0 <: Node end;

julia> axiom = A0() + B0();

julia> no_rules_graph = Graph(axiom = axiom);

julia> rule = Rule(A0, rhs = x -> A0() + B0());

julia> rules_graph = Graph(axiom = axiom, rules = rule);
```
