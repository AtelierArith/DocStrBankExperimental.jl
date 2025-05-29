```
densratiofunc(x_nu, x_de, dre; [optlib])
```

[`densratio`](@ref)と似ていますが、新しい未見のサンプル`x`で評価できる関数`r(x) = p_nu(x) / p_de(x)`を返します。

他にも[`densratio`](@ref)を参照してください。

### 注意事項

一部の推定器のみが`x_de`の外部で評価できる比率関数を定義します。
