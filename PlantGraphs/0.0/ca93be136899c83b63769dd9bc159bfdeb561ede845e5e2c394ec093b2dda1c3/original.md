```
Rule(nodetype; lhs = x -> true, rhs = x -> nothing, captures = false)
```

Create a replacement rule for nodes of type `nodetype`.

## Arguments

  * `nodetype`: Type of node to be matched.

## Keywords

  * `lhs`: Function or function-like object that takes a `Context` object and returns whether the node should be replaced or not (with `true` or `false`).
  * `rhs`: Function or function-like object that takes one or more `Context` objects and returns a replacement graph or `nothing`. If it takes several inputs, the first one will correspond to the node being replaced.
  * `captures`: Either `false` or `true` to indicate whether the left-hand side of the rule is capturing nodes in the context of the replacement node to be used for the construction of the replace graph.

## Details

See VPL documentation for details on rule-based graph rewriting.

## Return

An object of type `Rule`.

## Examples

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> rule = Rule(A, rhs = x -> A() + B());

julia> rules_graph = Graph(axiom = axiom, rules = rule);

julia> rewrite!(rules_graph);
```
