```
overlapwithcomputational(psum::PauliSum, onebitinds)
```

指定された `indices` で全てのビットが1で、他のビットが0の計算基底状態とのパウリ和の重なりを計算します。例えば、`overlapwithcomputational(psum, [1,2,4])` は `|1101000...>` との重なりを返します。
