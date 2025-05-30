```julia
struct Arg <: Moonshine.AbstractGenealogy
```

Ancestral recombination graph.

See also [`Tree`](@ref).

# Fields

  * `graph::Graphs.SimpleGraphs.SimpleDiGraph{Int32}`: Graph's topology
  * `latitudes::Vector{Float64}`: Vertices' latitudes
  * `recombination_mask::Vector{Moonshine.AncestralIntervals{Vector{IntervalSets.Interval{:closed, :open, Float64}}}}`: ∩-mask for ancestral intervals
  * `mrca::Base.RefValue{Int32}`: Arg's grand MRCA
  * `sequences::Vector{Moonshine.Sequence}`: Vertices' haplotypes
  * `ancestral_intervals::Dict{Graphs.SimpleGraphs.SimpleEdge{Int32}, Moonshine.AncestralIntervals{Vector{IntervalSets.Interval{:closed, :open, Float64}}}}`: Edges' ancestral intervals
  * `sample::Moonshine.Sample`: Associated [`Sample`](@ref)
  * `logdensity::Base.RefValue{DoubleFloats.Double64}`: Log-value of the associated pdf

# Constructors

!!! info
    Random constructor calls [`Sample`](@ref)'s random constructor.


!!! warning
    These **do not** actually build the arg. For that, see [`build!(rng, arg)`](@ref).


```julia
Arg(
    graph,
    latitudes,
    recombination_mask,
    mrca,
    sequences,
    ancestral_intervals,
    sample,
    logdensity
)
Arg(
    graph,
    latitudes,
    recombination_mask,
    mrca,
    sequences,
    ancestral_intervals,
    sample,
    logdensity
)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:43`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
Arg(tree)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:61`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

```julia
Arg(rng, n, μ, ρ, Ne, sequence_length)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Arg.jl:77`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl).

# Arguments

  * `tree`: coalescent [`Tree`](@ref)
  * other arguments are identical to [`Sample`](@ref)
