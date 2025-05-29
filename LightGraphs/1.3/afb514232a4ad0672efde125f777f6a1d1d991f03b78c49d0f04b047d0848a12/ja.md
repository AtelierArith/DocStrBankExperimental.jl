```
independent_set(g, MaximalIndependentSet(); seed=-1)
```

独立な頂点のランダムな集合を見つけます（隣接する頂点は存在しません）および独立性の特性を損なうことなく集合に頂点を挿入することができません。

### 実装ノート

[近似最大独立集合](https://en.wikipedia.org/wiki/Maximal_independent_set#Sequential_algorithm)を1回実行します。独立集合の頂点を表す頂点のベクトルを返します。

### パフォーマンス

実行時間: O(|V|+|E|) メモリ: O(|V|) 近似係数: maximum(degree(g))+1

### オプション引数

  * `seed >= 0`の場合、この値でランダムジェネレーターがシードされます。
