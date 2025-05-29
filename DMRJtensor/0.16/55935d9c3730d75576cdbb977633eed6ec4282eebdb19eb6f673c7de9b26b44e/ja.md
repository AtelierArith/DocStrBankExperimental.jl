```
expval = expect(dualpsi,psi,H[,Lbound=,Rbound=,order=])
```

任意の数のMPO `H` に対して <`dualpsi`|`H`|`psi`> を評価します。左境界 (`Lbound`) と右境界 (`Rbound`) を指定できます。`dualpsi` はアルゴリズム内で共役化されます。出力は期待値 `expval` です。

参照: [`overlap`](@ref)
