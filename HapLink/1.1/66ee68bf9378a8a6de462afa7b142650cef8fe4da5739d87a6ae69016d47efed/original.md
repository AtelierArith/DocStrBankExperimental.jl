```
simulate(
    pool::AbstractArray{Pseudoread},
    refseq::BioSequence,
    subcon::AbstractArray{Variation{S,T}};
    reverse_order::Union{Bool,Nothing}=nothing,
    overlap_min::Int64=0,
    overlap_max::Int64=500,
) where {S,T} -> Union{Haplotype{S,T},Nothing}
```

Creates a new set of [`Pseudoread`](@ref)s based on the `pool` of real reads spliced spliced together using maximum likelihood simulation.

# Arguments

  * `pool::AbstractArray{Pseudoread}`: A set of (presumably) real sequencing reads that will serve as pieces of the new simulated reads.
  * `refseq::BioSequence`: The reference against which all of the sequences in `pool` and `subcon` were aligned
  * `subcon::AbstractArray{Variation{S,T}}`: The subconsensus `Variation`s which are known to be both present in `pool` and real (i.e., not due to sequencing errors)

# Options

  * `reverse_order::Union{Bool,Nothing}=nothing`: Whether the splicing should start at the beginning or end of the reference sequence. If left blank, will randomly decide.
  * `overlap_min::Int64=0`: The amount that reads from `pool` are required to overlap in order to be spliced together. Can be negative, indicating that reads must be spaced apart by this amount, instead. -`overlap_max::Int64=500`: The amount that reads from pool can overlap before being discarded. Like `overlap_min`, can be negative.

# Returns

A `Haplotype{S,T}` representing the simulated read, or `nothing` if the simulation encountered a dead end.

# Extended help

The simulation procedure works by picking a read from `pool` that contains the first (if `reverse_order` is false, the last otherwise) variant from `subcon`. The procedure examines every position in `subcon` in ascending (or descending, if `reverse_order == true`) order until the chosen read no longer carries that position. The simulation will then, at random, pick a read from `pool` that contains the next position from `subcon` and that also *has matching variations at every position in `subcon` as the previous read*, as well as meets the overlap requirements. These two reads may differ in sites other than those in `subcon`: it is assumed that appropriate variant calling has already been performed and that any variation in those sites is due to sequencing error. The procedure repeats for each new read from `pool` until the simulation has simulated every position of `subcon`, or until it reaches a dead-end and cannot find a read that matches every requirement.
