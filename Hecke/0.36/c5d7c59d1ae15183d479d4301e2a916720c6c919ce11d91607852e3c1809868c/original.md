```
is_maximal_even(L::ZZLat, p::IntegerUnion) -> Bool, ZZLat
```

Given an integer lattice `L` with integral scale and a prime number `p`, return whether $L_p$ is even and has no proper overlattice satisfying this property.

If $L_p$ is not even, the second output is `L` by default. Otherwise, either `L` is maximal at `p` and the second output is `L`, or the second output is an overlattice `M` of `L` such that $M_p$ is even and $[M:L] = p$.
