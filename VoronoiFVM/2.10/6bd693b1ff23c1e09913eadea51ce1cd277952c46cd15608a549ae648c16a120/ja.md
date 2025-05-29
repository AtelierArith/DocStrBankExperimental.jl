```julia
freqdomain_impedance(
    impedance_system,
    ω,
    U0,
    excited_spec,
    excited_bc,
    excited_bcval,
    dmeas_stdy,
    dmeas_tran
)

```

インピーダンスの逆数を計算します。

  * excited*spec, excited*bc, excited_bcval は無視されます。

!!! 警告

これは非推奨です: [`impedance`](@ref) を使用してください。
