```julia
struct Tree <: Moonshine.AbstractGenealogy
```

Coalescent tree.

See also [`Arg`](@ref).

# Fields

  * `graph::Graphs.SimpleGraphs.SimpleDiGraph{Int32}`: Tree's topology
  * `latitudes::Vector{Float64}`: Vertices' latitudes
  * `sequences::Vector{Moonshine.Sequence}`: Vertices' haplotypes
  * `sample::Moonshine.Sample`: Associated [`Sample`](@ref)
  * `logdensity::Base.RefValue{DoubleFloats.Double64}`: Log-value of the associated pdf

# Constructors

!!! info
    Random constructor calls [`Sample`](@ref)'s random constructor.


!!! warning
    These **do not** actually build the tree. For that, see [`build!(rng, tree)`](@ref).


```julia
Tree(graph, latitudes, sequences, sample, logdensity)
Tree(graph, latitudes, sequences, sample, logdensity)
```

defined at [`packages/Moonshine/7JVTP/src/Tree.jl:42`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Tree.jl).

```julia
Tree(sample)
```

defined at [`packages/Moonshine/7JVTP/src/Tree.jl:54`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Tree.jl).

```julia
Tree(rng, n, μ, ρ, Ne, sequence_length)
```

defined at [`packages/Moonshine/7JVTP/src/Tree.jl:66`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Tree.jl).

# Arguments

Arguments are the same as for [`Sample`](@ref).
