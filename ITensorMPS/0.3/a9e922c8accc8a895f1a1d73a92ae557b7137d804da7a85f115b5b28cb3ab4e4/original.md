```
findsite(M::Union{MPS, MPO}, is)
```

Return the first site of the MPS or MPO that has at least one Index in common with the Index or collection of indices `is`.

To find all sites with common indices with `is`, use the `findsites` function.

# Examples

```julia
s = siteinds("S=1/2", 5)
ψ = random_mps(s)
findsite(ψ, s[3]) == 3
findsite(ψ, (s[3], s[4])) == 3

M = MPO(s)
findsite(M, s[4]) == 4
findsite(M, s[4]') == 4
findsite(M, (s[4]', s[4])) == 4
findsite(M, (s[4]', s[3])) == 3
```
