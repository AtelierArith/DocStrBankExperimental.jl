```
shift_estimator(df::DataFrame; shift=:shift, kwargs...)
shift_estimator(sim::PMCSimulation; kwargs...)
-> r::BlockingResult
```

`df.shift`のデータからシフト推定器を返します。キーワード引数`shift`を使用して、関連する列の名前を変更できます。他のキーワード引数は[`blocking_analysis`](@ref)に渡されます。[`BlockingResult`](@ref)を返します。

他に[`growth_estimator`](@ref)、[`projected_energy`](@ref)も参照してください。
