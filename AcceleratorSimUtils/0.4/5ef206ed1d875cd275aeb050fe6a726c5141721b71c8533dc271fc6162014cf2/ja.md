```
calc_γ(mass; E_tot = nothing, pc = nothing, β = nothing, E_kinetic = nothing) -> γ
calc_γ(species; E_tot = nothing, pc = nothing, β = nothing, E_kinetic = nothing) -> γ
```

粒子の相対論的ガンマ因子を返します。引数には `E_tot`（全エネルギー）、`pc`（運動量*c）、`β`（速度/c）、または `E_kinetic`（運動エネルギー）を指定できます。オプションの引数 `E_tot`、`pc`、`β`、または `E_kinetic` のうち、1つだけを設定する必要があります。

すべての引数は `Numbers` ですが、`species` 引数は `Species` 型です。`mass` 引数は `energy/c^2` の単位です。

また、関数 `calc_pc`、`calc_β`、`calc_β1`、`calc_E_kinetic`、および `calc_γ` も参照してください。
