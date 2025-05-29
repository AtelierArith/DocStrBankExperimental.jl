粒子が[`is_boson`](@ref)であることを示す具体的な型で、偏光が不定であり、微分断面積の計算は、問題の粒子の方向（[`Incoming`](@ref)または[`Outgoing`](@ref)）に応じて、すべての偏光を平均または合計する必要があります。

```jldoctest
julia> using QEDbase

julia> AllPol()
all polarizations
```

!!! info "エイリアス"
    `AllPolarization`の組み込みエイリアスがあります：

    ```jldoctest
    julia> using QEDbase

    julia> AllPolarization === AllPol
    true
    ```

