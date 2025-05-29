```
opLDL(M, [check=false])
```

存在する場合、LDLᵀ因子分解を使用して対称行列の逆を線形演算子として計算します。因子分解は一度だけ計算されます。オプションの `check` 引数は、安価なエルミート性チェックを実行します。

Mがスパースで実数の場合、[`LDLFactorizations.jl`](https://github.com/JuliaSmoothOptimizers/LDLFactorizations.jl)を使用するために、上三角行列のみを保存する必要があります：

```
using LDLFactorizations
triu!(M)
opLDL(Symmetric(M, :U))
```
