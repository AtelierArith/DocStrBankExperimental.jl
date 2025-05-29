```
findsites(M::Union{MPS, MPO}, is)
```

Return the sites of the MPS or MPO that have indices in common with the collection of site indices `is`.

# Examples

```julia
s = siteinds("S=1/2", 5)
ψ = random_mps(s)
findsites(ψ, s[3]) == [3]
findsites(ψ, (s[4], s[1])) == [1, 4]

M = MPO(s)
findsites(M, s[4]) == [4]
findsites(M, s[4]') == [4]
findsites(M, (s[4]', s[4])) == [4]
findsites(M, (s[4]', s[3])) == [3, 4]
```
