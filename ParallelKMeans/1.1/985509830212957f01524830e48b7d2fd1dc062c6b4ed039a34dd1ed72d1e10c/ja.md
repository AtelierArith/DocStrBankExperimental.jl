```
Hamerly()
```

Hamerlyアルゴリズムの実装で、"Hamerly, Greg. (2010). Making k-means Even Faster. Proceedings of the 2010 SIAM International Conference on Data Mining. 130-140. 10.1137/1.9781611972801.12."に基づいています。

このアルゴリズムは、Lloydアルゴリズムに比べてはるかに速い収束を提供し、メモリフットプリントの増加は比較的小さいです。特に、低次元から中次元の入力データに適しています。

`kmeans`関数で直接使用できます。

```julia
X = rand(30, 100_000)   # 30次元の100_000個のランダムポイント

kmeans(Hamerly(), X, 3) # 3つのクラスタ、Hamerlyアルゴリズム
```
