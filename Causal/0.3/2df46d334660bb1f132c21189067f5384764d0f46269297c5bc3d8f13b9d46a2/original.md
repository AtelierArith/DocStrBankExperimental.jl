```julia
struct Branch{NP, IP, LN<:(AbstractVector{<:Causal.Link})}
```

Constructs a `Branch` connecting the first and second element of `nodepair` with `links`. `indexpair` determines the subindices by which the elements of `nodepair` are connected.

# Fields

  * `nodepair::Any`: Node pair connected by the branch
  * `indexpair::Any`: Indices of output and input ports
  * `links::AbstractVector{<:Causal.Link}`: Links of the branch
