```
waveplate([T=Float64], δ=0, θ=0)
```

角度 `θ`（ラジアン）に合わせてファースト軸が整列された一般的な位相遅延器（波板）で、スロー軸に沿った位相遅延 `δ`（ラジアン）を持ちます。

# 例

```jldoctest
julia> M = waveplate(π);

julia> M ≈ hwp()
true

julia> M = waveplate(π/2, π/4);

julia> M ≈ qwp(π/4)
true
```

# 参照

[`hwp`](@ref), [`qwp`](@ref), [`mirror`](@ref)
