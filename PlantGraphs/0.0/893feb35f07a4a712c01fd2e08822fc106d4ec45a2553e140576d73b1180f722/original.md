```
ancestor(c::Context; condition = x -> true, max_level::Int = typemax(Int))
```

Returns the first ancestor of a node that matches the `condition`. Intended to be used within a rule or query.

## Arguments

  * `c::Context`: Context associated to a node in a dynamic graph.

## Keywords

  * `condition`: An user-defined function that takes a `Context` object as input and returns `true` or `false`.
  * `max_level::Int`: Maximum number of steps that the algorithm may take when traversing the graph.

## Details

If `has_ancestor()` returns `false` for the same node and `condition`, `ancestor()` will return `missing`, otherwise it returns the `Context` associated to the matching node

## Returns

Return a `Context` object or `missing`.

## Examples

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> axiom = A1(1) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> function qfun(n)
           na = ancestor(n, condition = x -> (data(x).val == 1))
           if !ismissing(na)
               data(na) isa B1
           else
               false
           end
       end;

julia> Q1 = Query(A1, condition = qfun);

julia> R1 = apply(g, Q1);

julia> Q2 = Query(B1, condition = qfun);

julia> R2 = apply(g, Q2);
```
