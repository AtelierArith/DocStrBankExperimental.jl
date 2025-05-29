```
confint(cb::SuptQuantileBootBand, draws::AbstractMatrix; level::Real=0.9, kwargs...)
```

モンティエル・オレアとプラグボルグ・ミュラー（2019）のアルゴリズム2に基づく、分位点ベースのブートストラップ実装を用いて、sup-t信頼帯を計算します。ポイント推定のブートストラップ `draws` は、各列が同じドローからのポイント推定のベクトルである行列である必要があります。下限と上限に加えて、ポイントごとの信頼レベル（信頼帯からの区間がポイントごとの信頼区間として見られるとき）が第3のオブジェクトとして返されます。

この手続きは、指定された信頼レベルを持つバンドを求めるための根探索問題を解くことを含みます。これは、[`Roots.jl`](https://github.com/JuliaMath/Roots.jl) の `find_zero` 関数を使用して達成されます。この問題を解くために使用されるデフォルトのブレッキング区間（または開始点）は、キーワード引数 `x0` を指定することで上書きできます。`Roots.jl` のソルバーは、キーワード引数 `solver` で指定できます。その他の追加のキーワード引数は `find_zero` に渡されます。

# 参考文献

  * Montiel Olea, José Luis and Mikkel Plagborg-Møller. 2019. "Simultaneous Confidence Bands: Theory, Implementation, and an Application to SVARs." Journal of Applied Econometrics 34 (1): 1-17.

```
