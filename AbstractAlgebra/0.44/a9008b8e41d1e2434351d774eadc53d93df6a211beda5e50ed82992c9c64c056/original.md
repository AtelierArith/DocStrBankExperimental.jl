```
remove(f::T, p::T) where T <: RingElem
```

Return a pair `v, q` where $p^v$ is the highest power of $p$ dividing $f$ and $q$ is the cofactor after $f$ is divided by this power.

See also [`valuation`](@ref), which only returns the valuation.
