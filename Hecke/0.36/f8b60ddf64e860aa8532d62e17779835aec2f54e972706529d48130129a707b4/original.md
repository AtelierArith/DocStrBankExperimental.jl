```
coxeter_number(ADE::Symbol, n) -> Int
```

Return the Coxeter number of the corresponding ADE root lattice.

If $L$ is a root lattice and $R$ its set of roots, then the Coxeter number $h$ is $|R|/n$ where `n` is the rank of $L$.

# Examples

```jldoctest
julia> coxeter_number(:D, 4)
6

```
