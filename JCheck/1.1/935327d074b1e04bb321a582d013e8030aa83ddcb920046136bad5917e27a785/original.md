```
Quickcheck(desc; rng=GLOBAL_RNG, n=100, serialize_fails=true)
```

Constructor for type [`Quickcheck`](@ref).

# Arguments

  * `desc::AbstractString`: description for the instance
  * `rng::AbstractRNG`: PRNG used to generate inputs
  * `n::Int`: number of random inputs to generate
  * `serialize_fails::Bool`: if true, serialize failing inputs to a JLSO file

# Examples

```jldoctest
julia> qc = Quickcheck("A Test")
A Test: 0 predicate and 0 free variable.
```
