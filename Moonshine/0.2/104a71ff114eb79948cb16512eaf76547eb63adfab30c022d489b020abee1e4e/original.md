```julia
struct Sample <: AbstractVector{Moonshine.Sequence}
```

Contain a sample of haplotypes and informations about them.

Implements [the iteration interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) and [the array interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array).

# Fields

  * `H::Vector{Moonshine.Sequence}`: Vector of haplotypes
  * `μ::Float64`: Unscaled (per-locus) mutation rate
  * `ρ::Float64`: Unscaled (per-locus) recombination rate
  * `Ne::Float64`: Effective population size
  * `sequence_length::Float64`: Sequence length
  * `positions::Vector{Float64}`: Marker's positions
  * `coefs::Tuple{Float64, Float64}`: Coefficients for positions' line

# Constructors

!!! info
    Random constructor sample sequences via [msprime](https://tskit.dev/msprime/docs/stable/intro.html) using a [binary mutation model](https://tskit.dev/msprime/docs/stable/api.html#msprime.BinaryMutationModel).


```julia
Sample(H, μ, ρ, Ne, sequence_length, positions, coefs)
Sample(H, μ, ρ, Ne, sequence_length, positions, coefs)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:33`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
Sample(H; μ, ρ, Ne, sequence_length, positions)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:49`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
Sample(ts)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:64`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

```julia
Sample(rng, n, μ, ρ, Ne, sequence_length)
```

defined at [`packages/Moonshine/7JVTP/src/Sample.jl:102`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sample.jl).

where:

  * `n`: number of sequences
  * `rng`: random number generator
  * `ts`: [Tree Sequence](https://tskit.dev/tskit/docs/latest/python-api.html#the-treesequence-class)
