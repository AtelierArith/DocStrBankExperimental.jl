```julia
get_system!(
    results::Union{InfrastructureSystems.Optimization.OptimizationProblemResults, PowerSimulations.SimulationProblemResults};
    kwargs...
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsType}

```

問題に使用されるシステムを返します。システムがまだデシリアライズされていないか、[`set_system!`](@ref) で設定されていない場合は、デシリアライズして保存します。

シミュレーションがすべてのシステムをファイルにシリアライズするように構成されている場合、返されるシステムにはすべてのデータが含まれます。そうでない場合、返されるシステムには時系列データを除くすべてのデータが含まれます。
