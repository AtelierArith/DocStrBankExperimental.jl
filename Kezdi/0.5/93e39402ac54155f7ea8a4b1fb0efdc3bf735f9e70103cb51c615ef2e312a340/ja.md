```
keep_only_values(x::AbstractVector) -> AbstractVector
```

`x`の値のみを含むベクトルを返し、`missing`値、`nothing`、`Inf`、および`NaN`を除外します。
