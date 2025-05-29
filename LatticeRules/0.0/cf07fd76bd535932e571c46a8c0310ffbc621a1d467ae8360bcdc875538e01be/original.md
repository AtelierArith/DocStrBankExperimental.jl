```
LatticeRule32(z, s, n)
LatticeRule32(z, s)
LatticeRule32(z)
```

Returns a rank-1 lattice rule in `s` dimensions with generating vector `z` and at most `n` points.

When no maximum number of points `n` is provided, we assume `n = typemax(UInt32) = 2^32 - 1`. When no number of dimensions `s` is provided, we assume `s = length(z)`. 

!!! info
    Technically, we return an extensible lattice sequence where the `k`-th point is transformed using the gray coded radical inverse function. This has the advantage that we can add points to the lattice without changing the already computed points.


More generating vectors can be found online [here](https://web.maths.unsw.edu.au/~fkuo/lattice/index.html) or [here](https://people.cs.kuleuven.be/~dirk.nuyens/qmc-generators/).

# Examples

```jldoctest; setup = :(using LatticeRules; import Random; Random.seed!(1))
julia> lattice_rule = LatticeRule32([UInt32(1), UInt32(5)], 2, 8) # Fibonacci lattice
LatticeRule32{2}

julia> getpoint(lattice_rule, 2)
2-element Array{Float64,1}:
 0.25
 0.25

```

See also: [`getpoint`](@ref), [`ShiftedLatticeRule32`](@ref)
