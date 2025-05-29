```
generate_samples(t::SumProductTree, nsamples::Int)
```

Direct sampling configurations from a [`SumProductTree`](@ref) instance.

## Examples

```jldoctest; setup=:(using GenericTensorNetworks)
julia> using Graphs

julia> g= smallgraph(:petersen)
{10, 15} undirected simple Int64 graph

julia> t = solve(GenericTensorNetwork(IndependentSet(g)), ConfigsAll(; tree_storage=true))[];

julia> samples = generate_samples(t, 1000);

julia> all(s->is_independent_set(g, s), samples)
true
```
