```
PauliSum(nqubits::Int, terms::Dict)
```

`PauliSum`は、`nqubits`量子ビット上で作用するパウリ文字列の和を表す`struct`です。これは、パウリ文字列をキー、係数を値とする辞書Dict(Pauli string => coefficient}のラッパーであり、パウリ文字列は通常、効率の理由から符号なし整数です。
