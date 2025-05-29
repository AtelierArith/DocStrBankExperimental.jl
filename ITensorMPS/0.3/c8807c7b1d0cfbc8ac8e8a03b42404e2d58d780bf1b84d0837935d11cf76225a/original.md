```
movesite(::Union{MPS, MPO}, n1n2::Pair{Int, Int})
```

Create a new MPS/MPO where the site at `n1` is moved to `n2`, for a pair `n1n2 = n1 => n2`.

This is done with a series a pairwise swaps, and can introduce a lot of entanglement into your state, so use with caution.
