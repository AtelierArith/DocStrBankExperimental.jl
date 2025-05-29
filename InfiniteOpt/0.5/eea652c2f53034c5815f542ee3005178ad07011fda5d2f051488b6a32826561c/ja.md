```
parameter_refs(mref::MeasureRef)::Tuple
```

測定された式に関連する `mref` が依存する無限パラメータのタプルを返します。これは、測定データに含まれているものを除いた測定関数のパラメータ依存関係に対応します。

**例**

```julia-repl
julia> parameter_refs(meas)
(t,)
```
