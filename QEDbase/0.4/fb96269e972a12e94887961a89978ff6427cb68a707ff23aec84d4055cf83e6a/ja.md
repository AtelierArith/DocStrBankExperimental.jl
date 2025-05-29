粒子が[`is_fermion`](@ref)であることを示す具体的な型であり、スピンが不定であることを示し、微分断面積の計算は、問題の粒子の方向（[`Incoming`](@ref)または[`Outgoing`](@ref)）に応じて、すべてのスピンを平均または合計する必要があります。

```jldoctest
julia> using QEDbase

julia> AllSpin()
all spins
```
