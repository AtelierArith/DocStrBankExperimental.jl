`galois(c::Cyc,n::Integer)` は `c` に対して `ℚ (ζ_conductor(c))` のガロワー自己同型を適用し、すべての根を `n` 乗します。`n` は `conductor(c)` と互いに素である必要があります。

# 例

```julia-repl
julia> galois(1+E(4),-1) # galois(c,-1) は conj(c) と同じです
Cyc{Int64}: 1-ζ₄

julia> galois(root(5),2)==-root(5)
true
```
