```julia
addOdoFG!(fgl, odo; N, solvable, labels)

```

新しい変数ノードを作成し、オドメトリ制約因子を挿入します。これにより、新しいノードの最新のポーズシンボル x<k+1> が自動的にインクリメントされ、新しいノードと制約因子がタプルとして返されます。
