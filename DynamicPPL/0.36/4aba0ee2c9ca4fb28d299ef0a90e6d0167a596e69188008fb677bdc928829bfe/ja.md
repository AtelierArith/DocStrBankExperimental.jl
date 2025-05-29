```
value_iterator_from_chain(model::Model, chain)
value_iterator_from_chain(varinfo::AbstractVarInfo, chain)
```

`model`/`varinfo`の各変数に対して`chain`内の値のイテレータを返します。

# 例

```julia
julia> using MCMCChains, DynamicPPL, Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function demo_model(x)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, sqrt(s))
           for i in eachindex(x)
               x[i] ~ Normal(m, sqrt(s))
           end

           return s, m
       end
demo_model (generic function with 2 methods)

julia> model = demo_model([1.0, 2.0]);

julia> chain = Chains(rand(rng, 10, 2, 3), [:s, :m]);

julia> iter = value_iterator_from_chain(model, chain);

julia> first(iter)
OrderedDict{VarName, Any} with 2 entries:
  s => 0.580515
  m => 0.739328

julia> collect(iter)
10×3 Matrix{OrderedDict{VarName, Any}}:
 OrderedDict(s=>0.580515, m=>0.739328)  …  OrderedDict(s=>0.186047, m=>0.402423)
 OrderedDict(s=>0.191241, m=>0.627342)     OrderedDict(s=>0.776277, m=>0.166342)
 OrderedDict(s=>0.971133, m=>0.637584)     OrderedDict(s=>0.651655, m=>0.712044)
 OrderedDict(s=>0.74345, m=>0.110359)      OrderedDict(s=>0.469214, m=>0.104502)
 OrderedDict(s=>0.170969, m=>0.598514)     OrderedDict(s=>0.853546, m=>0.185399)
 OrderedDict(s=>0.704776, m=>0.322111)  …  OrderedDict(s=>0.638301, m=>0.853802)
 OrderedDict(s=>0.441044, m=>0.162285)     OrderedDict(s=>0.852959, m=>0.0956922)
 OrderedDict(s=>0.803972, m=>0.643369)     OrderedDict(s=>0.245049, m=>0.871985)
 OrderedDict(s=>0.772384, m=>0.646323)     OrderedDict(s=>0.906603, m=>0.385502)
 OrderedDict(s=>0.70882, m=>0.253105)      OrderedDict(s=>0.413222, m=>0.953288)

julia> # これは`Model`を`condition`するために使用できます。
       conditioned_model = model | first(iter);

julia> conditioned_model()  # <= 上記の`first(iter)`と同じ値が得られます
(0.5805148626851955, 0.7393275279160691)
```
