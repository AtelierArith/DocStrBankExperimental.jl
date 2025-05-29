```
calc_E_tot(mass; pc = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> E_tot
calc_E_tot(species; pc = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> E_tot
```

粒子の総エネルギーを返します（単位は `eV`）。`pc`（運動量*c）、`β`（速度/c）、`E_kinetic`（運動エネルギー）、または `γ`（相対論的因子）のいずれか一つが設定されている必要があります。オプション引数 `pc`、`β`、`E_kinetic`、または `γ` のうち、1つだけが設定されるべきです。すべての引数は `Numbers` ですが、`species` は `Species` 型です。

`mass` 引数は `energy/c^2` の単位です。

また、関数 `calc_pc`、`calc_β`、`calc_β1`、`calc_E_kinetic`、および `calc_γ` も参照してください。
