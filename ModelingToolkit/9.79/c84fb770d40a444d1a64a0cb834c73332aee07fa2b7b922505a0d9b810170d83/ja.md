```julia
observables(sys::ModelingToolkit.AbstractSystem) -> Any

```

システム `sys` とそのサブシステムの観測変数を取得します。これらは `unknowns(sys)` の観点から表現でき、明示的に解決する必要はありません。これは `observed(sys)` のすべての左辺と同等です。

関連情報として [`observed`](@ref) を参照してください。
