`Partition` は、非空で互いに素な集合の集合です。新しい `Partition` は、基底集合 `A` を指定し、`Partition(A)` を呼び出すことで作成されます。集合 `A` は、ある型 `T` の `Set{T}` または `BitSet` である場合があります。

パラメータ `A` は、リスト（一次元配列）でもかまいません。

さらに、非負整数 `n` に対して `Partition(n)` は集合 {1,2,...,n} の分割を作成します。

データ型 `Partition` は、基本的に `DataStructures.DisjointSets` 型のラッパーです。
