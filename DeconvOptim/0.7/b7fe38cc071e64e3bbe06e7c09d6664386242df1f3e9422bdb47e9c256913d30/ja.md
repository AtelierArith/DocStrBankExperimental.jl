```
Tikhonov(; <キーワード引数>)
```

この関数は、n次元配列のティホノフ正則化子を計算する関数を返します。

# 引数

  * `num_dims=2`:
  * `sum_dims=[1, 2]`: 合計を求める次元を含む配列
  * `weights=nothing`: 異なる次元の寄与に重みを付けるための重みを含む配列。`weights=nothing`の場合、すべての次元は同じ重みが付けられます。
  * `step=1`: 配列インデックスのステップ幅を示す整数
  * `mode="laplace"`: ティホノフ正則化子の異なるモードを考慮するための `"laplace"`、`"spatial_grad_square"`、`"identity"` のいずれか。デフォルトは `"laplace"` です。

# 例

第三次元が異なる寄与を持つ3Dデータセットのための正則化子を作成するには。

```julia-repl
julia> reg = Tikhonov(num_dims=2, sum_dims=[1, 2], weights=[1, 1], mode="identity");

julia> reg([1 2 3; 4 5 6; 7 8 9])
285
```
