```
 (graph,crefs)=graph_newton_schulz(
    k,
    T = ComplexF64;
    input = :A,
    Z = :Z,
    Q = :Q,
    V = :V,
)
```

行列 A の逆行列を近似するためのニュートン–シュルツ反復を `k` 回実行します（`input` で指定された名前）。すなわち、再帰関係

```
V_k+1 = V_k*(2*I - A*V_k),
```

は `V_0=A` で始まります。この再帰はグラフ操作を使用して実装されます。

```
Z_i=A*V_i
Q_i=2*I-Z_i
V_{i+1}=V_i*Q_i,
```

およびキーワード引数 `Z`、`Q`、`V` は、対応する中間ステップの名前付けを決定します。

**参考文献**

1. G. Schulz. "Iterative Berechnung der reziproken Matrix". Zeitschrift für Angewandte Mathematik und Mechanik, 13:57–59, 1933. DOI: [10.1002/zamm.19330130111](https://doi.org/10.1002/zamm.19330130111)
2. N. J. Higham. "Functions of Matrices". SIAM, Philadelphia, PA, 2008. DOI: [10.1137/1.9780898717778](https://doi.org/10.1137/1.9780898717778)
