```
sample(f, a, b; cost::AbstractCost=CompositeCost((UniformCost(a, b), VisvalingamCost(a, b, f(a), f(b))), (1, 100)), tol=1e-3, maxsamples=10000)
```

関数 `f` を区間 `[a, b]` で指定されたコスト関数を使用してサンプリングします。サンプリングプロセスは、最大コストが許容誤差 `tol` 未満になるか、最大サンプル数 `maxsamples` に達するまで続きます。

# 引数

  * `f`: サンプリングされる関数。
  * `a`: 区間の開始。
  * `b`: 区間の終了。
  * `cost::AbstractCost`: 使用されるコスト関数。デフォルトは `UniformCost` と `VisvalingamCost` を組み合わせた複合コストです。
  * `tol`: 最大コストの許容誤差。デフォルトは `1e-3`。
  * `maxsamples`: 最大サンプル数。デフォルトは `10000`。

# 戻り値

  * `x`: サンプルポイントのベクトル。
  * `y`: サンプルポイントでの関数値のベクトル。
