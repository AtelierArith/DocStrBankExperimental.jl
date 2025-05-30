```julia
struct Sequence
```

Sequence of biallelic genetic markers (haplotype).

Implement [the iteration interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) as well as standard bitwise operations.

!!! info
    Random constructors sample marker's states via [`Random.bitrand`](@extref).


# Fields

  * `data::BitVector`

# Constructors

```julia
Sequence(data)
Sequence(data)
```

defined at [`packages/Moonshine/7JVTP/src/Sequence.jl:48`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sequence.jl).

```julia
Sequence()
```

defined at [`packages/Moonshine/7JVTP/src/Sequence.jl:187`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sequence.jl).

```julia
Sequence(undef, n)
```

defined at [`packages/Moonshine/7JVTP/src/Sequence.jl:189`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sequence.jl).

```julia
Sequence(rng, n)
```

defined at [`packages/Moonshine/7JVTP/src/Sequence.jl:191`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sequence.jl).

```julia
Sequence(rng, minlength, maxlength)
```

defined at [`packages/Moonshine/7JVTP/src/Sequence.jl:193`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sequence.jl).

where:

  * `n`: number of markers
  * `rng`: random number generator
  * `minLength, maxLength`: bounds for sequence length
