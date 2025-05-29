```
has_descendant(c::Context; condition = x -> true, max_level::Int = typemax(Int))
```

Check if a node has a descendant that matches the optional condition. Intended to be used within a rule or query.

## Arguments

  * `c::Context`: Context associated to a node in a dynamic graph.

## Keywords

  * `condition`: An user-defined function that takes a `Context` object as input and returns `true` or `false`.
  * `max_level::Int`: Maximum number of steps that the algorithm may take when traversing the graph.

## Details

This function traverses the graph from the node associated to `c` towards the leaves of the graph until a node is found for which `condition` returns `true`. If no node meets the condition, then it will return `false`. The defaults values for this function are such that the algorithm always returns `true` after one step (unless it is applied to a leaf node) in which case it is equivalent to calling `has_children` on the node.

The number of levels that the algorithm is allowed to traverse is capped by `max_level` (mostly to avoid excessive computation, though the user may want to specify a meaningful limit based on the topology of the graphs being used).

The function `condition` should take an object of type `Context` as input and return `true` or `false`.

## Returns

Return a tuple with two values a `Bool` and an `Int`, the boolean indicating whether the node has an ancestor meeting the condition, the integer indicating the number of levels in the graph separating the node an its ancestor.

## Examples

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(2) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> function qfun(n)
           has_descendant(n, condition = x -> data(x).val == 1)[1]
       end;

julia> Q1 = Query(A1, condition = qfun);

julia> R1 = apply(g, Q1);

julia> Q2 = Query(B1, condition = qfun);

julia> R2 = apply(g, Q2);
```
