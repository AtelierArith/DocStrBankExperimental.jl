```
LazyKet(b, kets)
```

ketsのテンソル積の遅延実装。

サブケットは`kets`フィールドに格納されます。このようなケットの主な目的は、期待値などの大きな積状態の単純な計算です。これは、QuantumCumulants.jlで数値的初期状態を計算するために使用されます（QuantumCumulants.initial_valuesを参照）。
