```
distance_sampling(x,m,sampling)

xから貪欲な距離基準に基づいてサイズmのランダムなサブセットを選択します。最初のポイントは均等に選択されます。その後、sampling == :farthestの場合、各ステップで選択されるポイントは、現在選択されているすべてのポイントから最も遠いポイントです。sampling == :d2の場合、アルゴリズムはD²サンプリング [vassilvitskii2006k](@vassilvitskii2006k) であり、最も遠いポイントサンプリングの緩和された確率的バージョンです（確率が二乗距離に比例してポイントを選択します）。
```

```@example
x = rand(2, 200);
ind = distance_sampling(ColVecs(x), 40, :farthest)
scatter(x[1, :], x[2, :]; marker_z=map((v) -> v ∈ ind, 1:size(x, 2)), legend=:none)
```
