```
KronTrav(A,B,C...)
```

は、係数が `DiagTrav` のように順序付けられたクロンカー積を表します。例えば、`KronTrav(A,B) * DiagTrav(X)` は `B*X*A'` と同じ演算子を表しますが、`X` の右下は無視されます。
