```
raviartthomas(mesh, cellpairs::Array{Int,2})
```

入力 `mesh` 上に RT 基底を構築します。i 番目の RT 基底関数は、メッシュ上のセル `cellpairs[1,i]` から `cellpairs[2,i]` への電流分布を表します。

`RTBasis` 型のオブジェクトを返します。これは、メッシュとセルペアに対応する Shape オブジェクトのペアを含み、ソルバーによって必要とされるときに正確な基底関数を計算するために必要な係数とインデックスを含んでいます。
