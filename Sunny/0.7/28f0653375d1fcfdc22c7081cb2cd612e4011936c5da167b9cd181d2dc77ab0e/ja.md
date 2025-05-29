```
add_sample!(sc::SampledCorrelations, sys::System)
add_sample!(sc::SampledCorrelationsStatic, sys::System)
```

`sys`のスピン配置に対するペア相関データを測定し、これらの統計を`sc`に蓄積します。動的な[`SampledCorrelations`](@ref)の場合、提供されたスピン軌道の時間積分を行い、空間と時間の両方で相関を記録します。対照的に、[`SampledCorrelationsStatic`](@ref)は、提供された単一のスピン配置に対してのみ空間的相関を記録します。

時間積分は、`sys`のスピン配置をその場で更新します。この変化を避けるために、`add_sample!`を呼び出す前に[`clone_system`](@ref)を呼び出すことを検討してください。
