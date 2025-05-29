```
getpoint(lattice_rule, k)
```

`lattice_rule`の`k`-番目の点を取得します。

!!! note
    代替構文は`getindex(lattice_rule, k)`または`lattice_rule[k]`であり、これにより準モンテカルロ推定量$E[f]$のためのワンライナー`Q = mean(f.(lattice_rule[0:N-1]))`を書くことができます。


```jldoctest; setup = :(using LatticeRules)
julia> lattice_rule = LatticeRule32(2)
LatticeRule32{2}

julia> getpoint(lattice_rule, 3)
2-element Array{Float64,1}:
 0.75
 0.25

```

参照: [`LatticeRule32`](@ref), [`ShiftedLatticeRule32`](@ref)
