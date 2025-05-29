```
iterative_gdtw!(data; max_iters = data.max_iters, verbose = data.verbose) -> cost
```

`max_iters` 回の反復で GDTW アルゴリズムを実行し、結果のコストを返します。`data.cache` の [`GDTWWorkspace`](@ref) を使用し、`data.warp` ベクトルを更新します。ここで、`data` は通常 [`prepare_gdtw`](@ref) によって取得されます。

同じ `data` に対して、より高い値の `max_iters` で複数回呼び出すことができ、計算を最初からやり直すことなく洗練させることができ、収束を確認するのに便利です。

## 例

```julia
data = prepare_gdtw(x,y; max_iters = 3)
cost3 = iterative_gdtw!(data) # 3 回の反復を実行し、コストを返す
cost10 = iterative_gdtw!(data; max_iters = 10) # さらに 7 回の反復を実行し、コストを返す
ϕ, ψ = gdtw_warpings(data)

# 同等に、
cost10, ϕ, ψ = gdtw(x,y; max_iters = 10)
```
