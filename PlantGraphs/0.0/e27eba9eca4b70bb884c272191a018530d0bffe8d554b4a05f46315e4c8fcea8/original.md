```
Query(N::DataType; condition = x -> true)
```

Create a query that matches nodes of type `nodetype` and a `condition`.

## Arguments

  * `N::DataType`: Type of node to be matched.

## Keywords

  * `condition`: Function or function-like object that checks if a node should be selected.

## Details

If the `nodetype` should refer to a concrete type and match one of the types stored inside the graph. Abstract types or types that are not contained in the graph are allowed but the query will never return anything.

The `condition` must be a function or function-like object that takes a `Context` as input and returns `true` or `false`. The default `condition` always return `true` such that the query will

## Returns

It returns an object of type `Query`. Use `apply()` to execute the query on a dynamic graph.

# Examples

```jldoctest
julia> struct A <: Node end;

julia> struct B <: Node end;

julia> axiom = A() + B();

julia> g = Graph(axiom = axiom);

julia> query = Query(A);

julia> apply(g, query);
```
