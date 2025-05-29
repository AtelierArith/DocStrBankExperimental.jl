```
checkcontractible(A, iA, conjA, B, iB, conjB, label)
```

2つのテンソル `opA(A)` と `opB(B)` が、それぞれのインデックス `iA` と `iB` を収束させるために互換性があるかどうかを確認し、そうでない場合はエラーをスローします。操作 `opA` は `conjA` が `false` の場合は `identity` として機能し、`conjA` が `true` の場合は `conj` として機能します; 操作 `opB` は同様に `conjB` によって決定されます。
