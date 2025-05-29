```
eigenvector_centrality(g)
```

グラフ `g` の固有ベクトル中心性を計算します。

固有ベクトル中心性は、隣接ノードの中心性に基づいてノードの中心性を計算します。ノード `i` の固有ベクトル中心性は、方程式 $\mathbf{Ax} = λ \mathbf{x}$ における $\mathbf{x}$ の $i^{th}$ 要素であり、ここで $\mathbf{A}$ はグラフ `g` の隣接行列で、固有値は λ です。

ペロン–フロベニウス定理により、λ が隣接行列 $\mathbf{A}$ の固有ベクトルに関連する最大固有値である場合、唯一かつ正の解が存在します。

### 参考文献

  * Phillip Bonacich: Power and Centrality: A Family of Measures.   American Journal of Sociology 92(5):1170–1182, 1986   http://www.leonidzhukov.net/hse/2014/socialnetworks/papers/Bonacich-Centrality.pdf
  * Mark E. J. Newman: Networks: An Introduction.      Oxford University Press, USA, 2010, pp. 169.
