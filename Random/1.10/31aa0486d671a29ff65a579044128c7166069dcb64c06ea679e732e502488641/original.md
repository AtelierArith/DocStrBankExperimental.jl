```
Xoshiro(seed)
Xoshiro()
```

Xoshiro256++ is a fast pseudorandom number generator described by David Blackman and Sebastiano Vigna in "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021. Reference implementation is available at http://prng.di.unimi.it

Apart from the high speed, Xoshiro has a small memory footprint, making it suitable for applications where many different random states need to be held for long time.

Julia's Xoshiro implementation has a bulk-generation mode; this seeds new virtual PRNGs from the parent, and uses SIMD to generate in parallel (i.e. the bulk stream consists of multiple interleaved xoshiro instances). The virtual PRNGs are discarded once the bulk request has been serviced (and should cause no heap allocations).

# Examples

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
