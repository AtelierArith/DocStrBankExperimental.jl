```
calc_E_kinetic(mass; E_tot = nothing, pc = nothing, β = nothing, γ = nothing) -> E_kinetic
calc_E_kinetic(species; E_tot = nothing, pc = nothing, β = nothing, γ = nothing) -> E_kinetic
```

粒子の運動エネルギーを `eV` で返します。引数のいずれか一つ、`E_tot`（全エネルギー）、`pc`（運動量*c）、`β`（速度/c）、または `γ`（相対論的因子）を設定する必要があります。オプションの引数 `E_tot`、`pc`、`β`、または `γ` のうち、1つだけを設定する必要があります。

すべての引数は `Numbers` ですが、`species` は `Species` 型です。`mass` 引数は `energy/c^2` の単位です。

また、関数 `calc_E_tot`、`calc_pc`、`calc_β`、`calc_β1`、および `calc_γ` も参照してください。
