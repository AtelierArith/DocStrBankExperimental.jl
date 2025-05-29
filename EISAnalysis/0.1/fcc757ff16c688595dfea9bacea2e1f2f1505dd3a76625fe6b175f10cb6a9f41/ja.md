```
print_circuit(circuit)
```

回路の要素とそのパラメータを印刷します

# 引数

  * `circuit::Circuit`: 印刷される回路

# 例

```julia
using EISAnalysis
eval(initialize())
randles_circuit = 0.23r-r/0.2q
print_circuit(randles_circuit)

# 出力 

0.23r
1.0r
0.2 * q ^ 0.8
```
