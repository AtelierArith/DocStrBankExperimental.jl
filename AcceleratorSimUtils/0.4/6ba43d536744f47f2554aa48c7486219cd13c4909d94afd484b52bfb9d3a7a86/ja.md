```
calc_β(mass; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> β
calc_β(species; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> β
```

粒子の正規化された速度 `β` = `v/c` を返します。これは、`E_tot`（全エネルギー）、`pc`（運動量*c）、`E_kinetic`（運動エネルギー）、または `γ`（相対論的因子）のいずれかが与えられた場合です。オプションの引数 `E_tot`、`pc`、`E_kinetic`、または `γ` のうち、1つだけが設定されている必要があります。すべての引数は `Numbers` ですが、`species` は `Species` 型です。

`mass` 引数は `energy/c^2` の単位です。

また、関数 `calc_E_tot`、`calc_pc`、`calc_β1`、`calc_E_kinetic`、および `calc_γ` も参照してください。
