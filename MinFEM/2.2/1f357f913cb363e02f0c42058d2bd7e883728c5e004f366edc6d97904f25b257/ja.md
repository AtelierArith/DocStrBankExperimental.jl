```julia
solve!(S::MinFEM.PDESystem) -> Any

```

最初に、ディリクレ条件のための乗数を持つシステム行列を[assemble!](@ref)しようとします。システムが以前に使用されている場合、このステップはスキップされます。これは、システム行列の既存の因子分解に依存して決定されます。剛性行列またはディリクレ条件に変更がある場合は、最初に[refresh!](@ref)を呼び出すべきです。最後に、行列の因子分解を通じてシステムが解決されます。
