```
Quickcheck
```

Contain a set of properties to check through the generation of random input.

# Fields

  * `description::AbstractString`: description for the instance
  * `rng::AbstractRNG`: PRNG used to generate inputs
  * `predicates::PredsAssoc`: predicates to check
  * `variables::ArgsDict`: arguments used by the predicates
  * `n::Int`: number of random inputs to generate
  * `serialize_fails::Bool`: if true, serialize failing inputs to a JLSO file
