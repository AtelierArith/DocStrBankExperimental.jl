```
vals = count_unique(X)
```

`X`の各値の出現回数をカウントします。

#### 引数

  * `X`: イテラブル。

#### 戻り値

`Dict{eltype(X),Int}`で、キーは`X`のユニークな要素で、値はその出現回数です。

例: スニペット

```
stats = load_stats("mystats.jld2")
for solver ∈ keys(stats)
  @info "$solver statuses" count_unique(stats[solver].status)
end
```

は、`stats`内の各ソルバーの最終ステータスの出現回数を表示します。
