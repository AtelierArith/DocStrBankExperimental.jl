```
CrossRecurrenceMatrix(x, y, rthres; kwargs...)
```

軌道 `x` と `y` から交差再発行列を作成します。`rthres` と `kwargs` の可能な値については [`RecurrenceMatrix`](@ref) を参照してください。

交差再発行列は再発行列の二変量拡張です。長さ `n` と `m` の時系列 `x` と `y` に対して、これはブール値のスパースな `n×m` 行列です。

交差再発行列は、一般的に `rthres` に関係なく対称ではないことに注意してください。
