```
calc_1β(mass; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> 1-β
calc_1β(species; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> 1-β
```

粒子の `1 - β` = `1 - v/c` を、`E_tot`（全エネルギー）、`pc`（運動量*c）、`E_kinetic`（運動エネルギー）、または `γ`（相対論的因子）のいずれかが与えられた場合に返します。高エネルギー限界では、これはおおよそ `1/(2γ^2)` です。`calc_1β` は、高エネルギー限界において丸め誤差が問題にならないように計算されます。

オプション引数 `E_tot`、`pc`、`E_kinetic`、または `γ` のうち、1つだけを設定する必要があります。すべての引数は `Numbers` ですが、`species` は `Species` 型です。`mass` 引数は `energy/c^2` の単位です。

また、関数 `calc_E_tot`、`calc_pc`、`calc_β`、`calc_E_kinetic`、および `calc_γ` も参照してください。
