引数として供給されたもののテンソル積を作成します。

関数 `tensorproduct` はいくつかの簡略化を適用し、必ずしも Product 型を返すわけではありません。

単一の要素を持つ `tensorproduct(a)` は `a` を返します。

整数 `n` に対して、`tensorproduct(a, n)` は `tensorproduct(a, a, ..., a)` になります。型安全なバリアントは `tensorproduct(a, Val{N})` です。
