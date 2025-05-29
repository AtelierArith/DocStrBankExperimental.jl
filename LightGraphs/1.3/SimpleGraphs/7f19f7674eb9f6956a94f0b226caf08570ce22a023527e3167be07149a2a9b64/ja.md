```
random_configuration_model(n, ks)
```

`n` 頂点を持ち、各ノード `i` が次数 `k[i]` を持つランダム無向グラフを [configuration model](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf) に従って作成します。

### オプション引数

  * `seed=-1`: RNG シードを設定します。
  * `check_graphical=false`: true の場合、`k` がグラフィカル列であることを確認します

（[`isgraphical`](@ref) を参照）。

### パフォーマンス

時間計算量はおおよそ $\mathcal{O}(n \bar{k}^2)$ です。

### 実装ノート

$$
n \bar{k}
$$

個の `Int` の配列を割り当てます。
