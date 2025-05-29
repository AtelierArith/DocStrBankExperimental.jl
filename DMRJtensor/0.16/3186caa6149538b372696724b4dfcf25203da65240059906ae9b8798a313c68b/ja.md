```
expval = expect(psi,H[,Lbound=,Rbound=,order=])
```

任意の数のMPO `H` に対して <`psi`|`H`|`psi`> を評価します。左および右の境界（`Lbound` と `Rbound`）を指定できます。出力は期待値 `expval` です。

参照: [`overlap`](@ref)
