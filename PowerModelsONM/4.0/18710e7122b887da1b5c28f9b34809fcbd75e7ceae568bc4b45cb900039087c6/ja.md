```
build_solver_instances!(args::Dict{String,<:Any})::Dict{String,Any}
```

`entrypoint`内で使用するために、`args`辞書データ構造内でインプレースでオプティマイザを作成し、`args["solvers"]`に割り当てます。これは[`build_solver_instances`](@ref build_solver_instances)を使用します。
