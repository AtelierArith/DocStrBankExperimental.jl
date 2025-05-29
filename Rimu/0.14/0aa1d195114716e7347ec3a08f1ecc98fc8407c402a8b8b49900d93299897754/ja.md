```
step!(sm::PMCSimulation)::PMCSimulation
```

シミュレーションを1ステップ進めます。

[`solve!`](@ref)を呼び出すと、シミュレーションは最後のステップまで進むか、壁時間が超過するまで進みます。[`solve!`](@ref)を呼び出さずにシミュレーションを完了する場合、[`Rimu.finalize_report!`](@ref)を呼び出してシミュレーションレポートを最終化する必要があります。

他にも[`ProjectorMonteCarloProblem`](@ref)、[`init`](@ref)、[`solve!`](@ref)、[`solve`](@ref)、[`Rimu.PMCSimulation`](@ref)を参照してください。
