```
ReportDFAndInfo(; reporting_interval=1, info_interval=100, io=stdout, writeinfo=false) <: ReportingStrategy
```

デフォルトの [`ReportingStrategy`](@ref) は [`ProjectorMonteCarloProblem`](@ref) 用です。`reporting_interval` ごとに `DataFrame` に報告し、`info_interval` ごとに報告されたステップで `io` に情報メッセージを書き込みます（`writeinfo == false` の場合を除く）。フラグ `writeinfo` は、MPI コードでの情報メッセージの制御に役立ちます。例えば、`writeinfo =`[`is_mpi_root()`](@ref Rimu.is_mpi_root) を設定することで制御できます。

他に [`ProjectorMonteCarloProblem`](@ref)、[`ReportToFile`](@ref) も参照してください。
