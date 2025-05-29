```
zeroworkspace(model, plan)
```

与えられた `model` の各変数/ショックに対して [`TSeries`](@ref TimeSeriesEcon.TSeries) を含む [`Workspace`](@ref TimeSeriesEcon.Workspace) を作成します。これらは0に初期化されます。

シミュレーションには [`zerodata`](@ref) の使用をお勧めします。 [`zeroarray`](@ref) も参照してください。
