```
X = nonneg_lsq(A, B; gram=false, alg=:pivot, variant=:none, use_parallel=true, kwargs...)
X = nonneg_lsq(A'*A, A'*B; gram=true, ...)
```

行列 `X` を計算します。これは `vecnorm(A*X - B)` を最小化し、`X .>= 0` の制約を満たすもので、`A` は (m-by-k) 行列、`B` は (m-by-n) 行列です。代わりにベクトル `b` を供給することもできます。

## オプション引数

`alg`: 使用するアルゴリズムを指定するシンボル

  * `:pivot`: ブロックピボットアクティブセット法 (Kim & Park, 2011)
  * `:fnnls`: 高速アクティブセット法 (Bro & De Jong, 1997)
  * `:nnls`: 古典的アクティブセット法 (Lawson & Hanson, 1974)
  * `:admm`: 交互方向法 (例: Boyd et al., 2011)

`variant`: バリアントを指定するシンボル (これは `alg=:pivot` のみ適用可能で、潜在的な値は `:comb` または `:cache`)

`gram`: グラム行列 `A'*A`,`A'*B` をデータ行列 `A`,`B` の代わりに供給する場合は `true` に設定すべきブール値

`tol:` 非負制約のための許容誤差

`max_iter:` 関数が諦める前の最大反復回数

`use_parallel`: `B` に複数の列があり、`Threads.nthreads() > 1` の場合はスレッドを使用します。
