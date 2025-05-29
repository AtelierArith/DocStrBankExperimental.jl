```
maximal_even_lattice(L::ZZLat, p::IntegerUnion) -> ZZLat
```

Given an integer lattice `L` with integral scale and a prime number `p` such that $L_p$ is even, return an overlattice `M` of `L` which is maximal even at `p` and which agrees locally with `L` at all other places.
