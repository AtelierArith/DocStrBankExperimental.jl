```
StrictlyMinimumDistance([brute = false,] [metric = Euclidean(),])
```

[`set_distance`](@ref) で使用できる距離です。`StrictlyMinimumDistance` は、あるセットの点から他のセットの最も近い点までのすべての距離の中で最小の距離を返します。距離は指定されたメトリックを使用して計算されます。

`brute::Bool` 引数は、KDTreeベースのバージョンと、ブルートフォース（すべての距離を計算して最小のものを選ぶ）との間で計算を切り替えます。ブルートフォースは、次元が大きいか、点の数が少ないセットに対してより良いパフォーマンスを発揮します。カッティングポイントを決定することは簡単ではなく、単に [`set_distance`](@ref) 関数をベンチマークして決定することをお勧めします。

`brute = false` の場合、このメトリックは `SVector` の要素を持つ `StateSpaceSet` のみで機能します。

開発者向け: `set_distance` は、2番目のセットのKDTreeであるキーワード `tree2` を受け取ることができます。
