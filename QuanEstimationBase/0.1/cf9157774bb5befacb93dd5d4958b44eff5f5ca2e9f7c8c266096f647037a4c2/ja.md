```
MeasurementOpt(mtype=:Projection, kwargs...)
```

測定最適化。

  * `mtype`: 測定最適化のシナリオのタイプ。オプションは `:Projection`（デフォルト）、`：LC` および `:Rotation` です。
  * `kwargs...`: キーワードと対応するデフォルト値。`mtype=:Projection`、`mtype=:LC` および `mtype=:Rotation` の場合、`kwargs...` はそれぞれ `M=nothing`、`B=nothing, POVM_basis=nothing`、および `s=nothing, POVM_basis=nothing` です。
