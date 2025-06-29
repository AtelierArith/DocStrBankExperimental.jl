```
StochasticBlockModel{T,P}
```

SBMのパラメータをキャプチャする型です。各頂点はブロックに割り当てられ、エッジ `(i,j)` の確率は頂点 `i` と頂点 `j` のブロックラベルのみに依存します。

割り当てはnodemapに保存され、ブロックの親和性は `k` by `k` 行列としてaffinitiesに保存されます。

`affinities[k,l]` はブロック `k` の任意の頂点とブロック `l` の任意の頂点の間のエッジの確率です。

### 実装ノート

グラフはランダムに $i,j ∈ V$ を取り、確率 `affinities[nodemap[i],nodemap[j]]` でコインを裏返すことによって生成されます。
