```
rand([rng::AbstractRNG,]
      model::TraitSubstitutionModel,
      net::HybridNetwork;
      ntraits=1,
      keepinternal=true,
      checkpreorder=true)
```

Simulate evolution of discrete traits on a rooted evolutionary network based on the supplied evolutionary model. Trait sampling is uniform at the root.

optional arguments:

  * `ntraits`: number of traits to be simulated (default: 1 trait).
  * `keepinternal`: if true, export character states at all nodes, including internal nodes. if false, export character states at tips only.

output:

  * matrix of character states with one row per trait, one column per node; these states are *indices* in `model.label`, not the trait labels themselves.
  * vector of node labels (for tips) or node numbers (for internal nodes) in the same order as columns in the character state matrix

# examples

```jldoctest
julia> m1 = BinaryTraitSubstitutionModel(1.0, 2.0, ["low","high"]);

julia> net = readnewick("(((A:4.0,(B:1.0)#H1:1.1::0.9):0.5,(C:0.6,#H1:1.0::0.1):1.0):3.0,D:5.0);");

julia> using Random; Random.seed!(95);

julia> trait, lab = rand(m1, net)
([1 2 … 1 1], ["-2", "D", "-3", "-6", "C", "-4", "H1", "B", "A"])

julia> trait
1×9 Matrix{Int64}:
 1  2  1  1  2  2  1  1  1

julia> lab
9-element Vector{String}:
 "-2" 
 "D"  
 "-3" 
 "-6" 
 "C"  
 "-4" 
 "H1"
 "B"  
 "A"  
```
