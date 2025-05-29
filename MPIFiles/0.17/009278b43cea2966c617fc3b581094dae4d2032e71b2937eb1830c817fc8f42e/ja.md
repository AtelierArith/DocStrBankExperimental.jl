```julia
combine(
    tf1::MPIFiles.TransferFunction,
    tf2::MPIFiles.TransferFunction;
    interpolate
) -> Any

```

2つの`TransferFunctions`をチャネル次元に沿って結合します。interpolate=falseの場合、周波数サンプルが同一である場合にのみ機能します。
