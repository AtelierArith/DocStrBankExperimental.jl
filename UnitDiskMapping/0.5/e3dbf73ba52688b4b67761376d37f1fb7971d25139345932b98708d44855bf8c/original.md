```
map_factoring(M::Int, N::Int)
```

Setup a factoring circuit with M-bit `q` register (second input) and N-bit `p` register (first input). The `m` register size is (M+N-1), which stores the output. Call [`solve_factoring`](@ref) to solve a factoring problem with the mapping result.
