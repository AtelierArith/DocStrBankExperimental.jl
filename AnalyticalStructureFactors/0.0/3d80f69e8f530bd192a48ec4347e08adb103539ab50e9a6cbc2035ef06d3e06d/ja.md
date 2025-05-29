```
C_WCA_blip(ϕ::T, temperature::T, k::T; ν::Integer = 6) where {T<:AbstractFloat}
```

直接相関関数は、Verlet-Weiss補正を用いて効果的なハードスフィア系にマッピングするためのブリップ関数を用いたWCA近似を使用しています。
