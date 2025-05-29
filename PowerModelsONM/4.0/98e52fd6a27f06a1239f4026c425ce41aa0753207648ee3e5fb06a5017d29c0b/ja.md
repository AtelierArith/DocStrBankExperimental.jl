```
entrypoint(args::Dict{String,<:Any})::Dict{String,Any}
```

メインのONMアルゴリズムは、以下のステップを実行します：

  * [`initialize_output!`](@ref initialize_output!)
  * [`sanitize_args!`](@ref sanitize_args!)
  * [`setup_logging!`](@ref setup_logging!)
  * [`prepare_data!`](@ref prepare_data!)
  * [`build_solver_instances!`](@ref build_solver_instances!)
  * [`optimize_switches!`](@ref optimize_switches!)
  * [`optimize_dispatch!`](@ref optimize_dispatch!)
  * [`run_stability_analysis!`](@ref run_stability_analysis!)
  * [`run_fault_studies!`](@ref run_fault_studies!)
  * [`analyze_results!`](@ref analyze_results!)

もし`args["debug"]`が指定されている場合、すべてのデータ、結果などが含まれるファイルが"debug*onm*yyyy-mm-dd–HH-MM-SS.json"に書き込まれます。

すべての入力と出力を含む完全なデータ構造を返します。
