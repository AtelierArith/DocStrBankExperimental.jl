```
calc_pc(mass; E_tot = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> pc
calc_pc(species; E_tot = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> pc
```

与えられた `E_tot`（全エネルギー）、`β`（速度/c）、`E_kinetic`（運動エネルギー）、または `γ`（相対論的因子）のいずれかに基づいて、粒子の運動量*c（単位は `eV`）を返します。オプションの引数 `E_tot`、`β`、`E_kinetic`、または `γ` のうち、1つだけを設定する必要があります。すべての引数は `Numbers` ですが、`species` は `Species` 型です。

`mass` 引数はエネルギー/c^2 の単位です。

また、関数 `calc_E_tot`、`calc_β`、`calc_β1`、`calc_E_kinetic`、および `calc_γ` も参照してください。
