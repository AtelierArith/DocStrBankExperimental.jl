```
all_simple_paths(g, u, v; cutoff)  --> Graphs.SimplePathIterator
all_simple_paths(g, u, vs; cutoff) --> Graphs.SimplePathIterator
```

Returns an iterator that generates all  [simple paths](https://en.wikipedia.org/wiki/Path_(graph_theory)#Walk,_trail,_and_path) in  the graph `g` from a source vertex `u` to a target vertex `v` or iterable of target vertices `vs`. A simple path has no repeated vertices.

The iterator's elements (i.e., the paths) can be materialized via `collect` or `iterate`. Paths are iterated in the order of a depth-first search.

If the requested path has identical source and target vertices, i.e., if `u = v`, a zero-length path `[u]` is included among the iterates.

## Keyword arguments

The maximum path length (i.e., number of edges) is limited by the keyword argument `cutoff` (default, `nv(g)-1`). If a path's path length is greater than `cutoff`, it is omitted.

## Examples

```jldoctest allsimplepaths; setup = :(using Graphs)
julia> g = complete_graph(4);

julia> spi = all_simple_paths(g, 1, 4)
SimplePathIterator{SimpleGraph{Int64}}(1 → 4)

julia> collect(spi)
5-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 4]
 [1, 3, 2, 4]
 [1, 3, 4]
 [1, 4]
```

We can restrict the search to path lengths less than or equal to a specified cut-off (here,  2 edges):

```jldoctest allsimplepaths; setup = :(using Graphs)
julia> collect(all_simple_paths(g, 1, 4; cutoff=2))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [1, 3, 4]
 [1, 4]
```
