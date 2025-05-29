```
sysr = dsxvarsel(sys,ind)
```

順序 `n` の記述子系 `sys = (A-λE,B,C,D)` に対して、状態変数を `ind` で指定されたインデックスで選択することにより、順序 `nr = length(ind)` の記述子系 `sysr = (A[ind,ind]-λE[ind,ind],B[ind,:],C[:,ind],D)` を構築します。もし `ind` が長さ `n` の置換ベクトルであれば、`sysr` は `sys` と同じ伝達関数行列を持ち、状態変数が置換されます。
