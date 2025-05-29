```
random_configuration_model(n::Int, k::Vector{Int}, G=Graph; seed=-1, check_graphical=false)
```

[configuration model](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf) に従ってランダムな無向グラフを作成します。`n` 個の頂点を含み、頂点 `i` は次数 `k[i]` を持ちます。

`c = mean(k)` を定義すると、`nc` 個の `Int` の配列を割り当て、約 $nc^2$ の時間がかかります。

`check_graphical=true` の場合、`k` がグラフィカルな列であることを確認します（`is_graphical` を参照）。

`G` は結果のグラフの型です。
