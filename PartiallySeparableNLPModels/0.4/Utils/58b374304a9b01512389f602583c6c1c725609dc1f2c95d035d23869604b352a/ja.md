```
partitioned_structure = build_PartitionedDataTRPQN(expr_tree, n)
```

分割準備法信頼領域法を実行するために必要な構造を返します。これは、f(x) = ∑fᵢ(xᵢ)を表す式木`expr_tree`の部分的に分離可能な構造を見つけます。次に、必要な分割構造を割り当てます。分割行列のスパース行列を正しく定義するためには、問題のサイズ`n`が必要です。
