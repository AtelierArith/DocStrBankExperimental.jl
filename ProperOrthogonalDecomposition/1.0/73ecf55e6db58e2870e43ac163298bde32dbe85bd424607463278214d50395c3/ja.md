```
PODBasis{T}(coefficients::Matrix{T}, modes::Matrix{T})
```

適切な直交分解基を格納するためのデータ構造です。

POD基が表している元のデータは、モードを係数で右掛けすることによって再構成できます。すなわち、`A = P.modes*P.coefficients` です。
