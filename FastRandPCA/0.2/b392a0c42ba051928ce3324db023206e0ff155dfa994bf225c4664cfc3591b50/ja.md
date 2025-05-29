`eig_svd(A, [k]; [kwargs...])`

行列 `A` の特異値分解を、`svd(A' * A)` を推定することによって実行します。`k` が指定されている場合、Krylov反復ソルバーが使用され、`k` 個の最大特異値と対応する特異ベクトルのみが返されます。

スパース行列で動作するように設計されています。キーワード引数は `KrylovKit.svdsolve` に転送されます。

# 例

```julia-repl
using SparseArrays
eig_svd(sprand(100, 100, 0.2), 10)
```
