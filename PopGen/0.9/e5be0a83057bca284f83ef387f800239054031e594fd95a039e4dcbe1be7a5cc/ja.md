```
alleleaverage(data::PopData; rounding::Bool = true)
```

`PopData`の平均アレル数（'mean'）と標準偏差（`stdev`）のNamedTupleを返します。結果を丸めないには`rounding = false`を使用します。デフォルト（`true`）は4桁に丸めます。
