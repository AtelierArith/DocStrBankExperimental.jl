`galois(c::Cyc,n::Integer)`  applies  to  `c`  the  galois  automorphism  of `ℚ (ζ_conductor(c))`  raising  all  roots  of  unity  to the `n`-th power. `n` should be prime to `conductor(c)`.

# Examples

```julia-repl
julia> galois(1+E(4),-1) # galois(c,-1) is the same as conj(c)
Cyc{Int64}: 1-ζ₄

julia> galois(root(5),2)==-root(5)
true
```
