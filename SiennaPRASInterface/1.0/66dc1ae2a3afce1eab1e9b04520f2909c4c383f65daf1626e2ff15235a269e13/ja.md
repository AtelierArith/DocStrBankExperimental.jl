```
GeneratorStoragePRAS <: AbstractRAFormulation
```

シエナの中で、発電機とストレージのように振る舞うオブジェクトは、PRASのgeneratorstorageにマッピングされます。

発電機ストレージの定式化を追加するには、[`assign_to_gen_stor_matrices!`](@ref) 関数も追加する必要があります。

  * [`HybridSystemPRAS`](@ref)
  * [`HydroEnergyReservoirPRAS`](@ref)
