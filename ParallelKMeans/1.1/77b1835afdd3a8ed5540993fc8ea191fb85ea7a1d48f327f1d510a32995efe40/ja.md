```
Elkan()
```

Elkanアルゴリズムの実装、"Charles Elkan. 2003. Using the triangle inequality to accelerate k-means. In Proceedings of the Twentieth International Conference on International Conference on Machine Learning (ICML’03). AAAI Press, 147–153."に基づいています。

このアルゴリズムは、特に高次元データに対してLloydアルゴリズムよりもはるかに速い収束を提供します。`kmeans`関数で直接使用できます。

```julia
X = rand(30, 100_000)   # 30次元の100_000個のランダムポイント

kmeans(Elkan(), X, 3) # 3つのクラスタ、Elkanアルゴリズム
```
