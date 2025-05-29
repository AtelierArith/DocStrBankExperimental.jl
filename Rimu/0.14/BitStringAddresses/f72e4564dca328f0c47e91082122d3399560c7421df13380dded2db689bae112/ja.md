```
bose_hubbard_interaction(address)
```

$$
Σ_i n_i (n_i-1)
$$

を返して、Bose-Hubbardのオンサイト相互作用を計算します（$U$の前因子なしで）。

# 例

```jldoctest
julia> Hamiltonians.bose_hubbard_interaction(BoseFS{4,4}((2,1,1,0)))
2
julia> Hamiltonians.bose_hubbard_interaction(BoseFS{4,4}((3,0,1,0)))
6
```
