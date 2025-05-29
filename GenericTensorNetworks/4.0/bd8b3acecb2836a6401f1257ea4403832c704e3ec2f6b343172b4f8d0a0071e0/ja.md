```
generate_samples(t::SumProductTree, nsamples::Int)
```

[`SumProductTree`](@ref) インスタンスからの直接サンプリング構成。

## 例

```jldoctest; setup=:(using GenericTensorNetworks)
julia> using Graphs

julia> g= smallgraph(:petersen)
{10, 15} 無向単純 Int64 グラフ

julia> t = solve(GenericTensorNetwork(IndependentSet(g)), ConfigsAll(; tree_storage=true))[];

julia> samples = generate_samples(t, 1000);

julia> all(s->is_independent_set(g, s), samples)
true
```
