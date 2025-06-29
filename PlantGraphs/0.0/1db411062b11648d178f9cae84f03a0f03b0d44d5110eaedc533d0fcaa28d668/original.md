```
traverse(g::Graph; fun = () -> nothing, order = "any", ID = root_id(g))
```

Iterates over all the nodes in the graph and execute for the function `fun` on each node

## Arguments

  * `g::Graph`: The graph object that will be traversed.

## Keywords

  * `fun`: A function or function-like object defined by the user that will be applied to each node.
  * `order`: Order in which the nodes in the graph will be visited. It can be "any" (default), "dfs" (depth-first search) or "bfs" (breadth-first search).
  * `ID`: The ID of the node where the traveral should start. By default, traversal starts at the root of the graph.

## Details

When `order = "any` traveral happens in the order in which the nodes are stored in the graph. This order is arbitrary (it does not correspond to the order in which nodes are created) but it should be reproducible (i.e., the same code will store the nodes in the same order). For algorithms that require use `any = "dfs"` or `any = "bfs"`.

When `order = "dfs"` the traveral happens in a depth-first order. That is, all nodes in a branch of the graph are visited until reach a leaf node, then moving to the next branch. Hence, this algorithm should always generate the same result when applied to the same graph (assuming the user-defined function is not stochastic)

When `order = "bfs"` the traveral happens in a breadth-first order. That is, all nodes at a given depth of the the graph are visited first, then moving on to the next level. Hence, this algorithm should always generate the same result when applied to the same graph (assuming the user-defined function is not stochastic). For a version of this function that us depth-first order see `traverse_dfs`.

This function does not store any results generated by `fun`. Hence, if the user wants to keep track of such results, they should be stored indirectly (e.g., via a global variable or internally by creating a functor).

The function or function-like object provided by the user should take only one argument that corresponds to applying `data()` to each node in the graph. Several methods of such function may be defined for different types of nodes in the graph. Since the function will use the data stored in the nodes, relations among nodes may not be used as input. For algorithms where relations among nodes are important, the user should be using queries instead (see `Query` and general VPL documentation).

## Returns

This function returns nothing but `fun` may have side-effects.

## Examples

```jldoctest
julia> struct A1 <: Node val::Int end;

julia> struct B1 <: Node val::Int end;

julia> struct Foo
         vals::Vector{Int}
       end;

julia> function (f::Foo)(x)
         push!(f.vals, x.val)
       end;

julia> f = Foo(Int[]);

julia> axiom = A1(2) + (B1(1) + A1(3), B1(4));

julia> g = Graph(axiom = axiom);

julia> traverse(g, fun = f);

julia> traverse(g, fun = f, order = "dfs");

julia> traverse(g, fun = f, order = "bfs");
```
