```
inbounds(data::AbstractSimData, I::Tuple) -> Tuple{NTuple{2,Int}, Bool}
inbounds(data::AbstractSimData, I...) -> Tuple{NTuple{2,Int}, Bool}
```

座標を格納する前に[`SetCellRule`](@ref)のためにグリッドの境界をチェックします。

`Tuple`を返し、座標の`Tuple`と`Bool`を含みます - セルがグリッドの境界内にある場合は`true`、そうでない場合は`false`です。

[`BoundaryCondition`](@ref)のタイプ[`Remove`](@ref)は、座標を返し、グリッドの外にある座標をスキップするために`false`を返します。

[`Wrap`](@ref)は、現在の位置またはそのラップされた等価物を含むタプルを返し、常に境界内にあるため`true`を返します。
