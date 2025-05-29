```
label_propagation(g, maxiter=1000; rng=nothing, seed=nothing)
```

ラベル伝播アルゴリズムを使用したコミュニティ検出。最初のベクトルは各ノードに割り当てられたラベル番号であり、2番目のベクトルは各ノードの収束履歴です。収束が完了していない場合は、`maxiter` 回の反復後に返されます。

### 参考文献

  * [Raghavan et al.](http://arxiv.org/abs/0709.2938)
