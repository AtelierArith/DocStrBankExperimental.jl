```
statuses, avgs = quick_summary(stats; kwargs...)
```

`stats`内の各ソルバーに対して`count_unique`を呼び出し、いくつかの平均値を計算します。

#### 引数

  * `stats::Dict{Symbol,DataFrame}`: `bmark_solvers`によって返されるベンチマーク統計。

#### キーワード引数

  * `cols::Vector{Symbol}`: 平均を計算するソルバー統計の`DataFrame`列を示すシンボル。デフォルト: `[:iter, :neval_obj, :neval_grad, :neval_hess, :neval_hprod, :elapsed_time]`。

#### 戻り値

  * `statuses::Dict{Symbol,Dict{Symbol,Int}}`: `stats`内の各ソルバーの各最終ステータスの出現回数の辞書。この辞書の各値は`count_unique`によって返されます。
  * `avgs::Dict{Symbol,Dict{Symbol,Float64}}`: 各ソルバーのすべての問題にわたるパフォーマンス測定の平均を含む辞書。各`avgs[solver]`は`Dict{Symbol,Float64}`で、測定値はキーワード引数`cols`で指定されたものであり、値はすべての問題にわたるそれらの測定値の平均です。

例: スニペット

```
statuses, avgs = quick_summary(stats)
for solver ∈ keys(stats)
  @info "statistics for" solver statuses[solver] avgs[solver]
end
```

は、各ソルバーのクイックサマリーと平均を表示します。
