```
dbscan(points::AbstractMatrix, radius::Real;
       [metric=Euclidean()],
       [min_neighbors=1], [min_cluster_size=1],
       [nntree_kwargs...]) -> DbscanResult
```

`points`をDBSCAN（ノイズを伴うアプリケーションのための密度ベースの空間クラスタリング）アルゴリズムを使用してクラスタリングします。

## 引数

  * `points`: `metric`が指定されている場合、各列が点の*d*-次元座標である*d×n*行列; `metric=nothing`の場合、点間のペアワイズ距離の*n×n*行列
  * `radius::Real`: 隣接半径; この距離内の点は隣人と見なされます

アルゴリズムを制御するためのオプションのキーワード引数:

  * `metric`（デフォルトは`Euclidean()`）: 使用する点の距離メトリック、`nothing`は`points`が*n×n*の事前計算された距離行列であることを意味します
  * `min_neighbors::Integer`（デフォルトは1）: 点をクラスタの「コア」に割り当てるために必要な最小隣人数
  * `min_cluster_size::Integer`（デフォルトは1）: クラスタ内の最小点数; 点数が少ないクラスタ候補は破棄されます
  * `nntree_kwargs...`: `KDTree`コンストラクタのためのパラメータ（`leafsize`など）

## 例

```julia
points = randn(3, 10000)
# DBSCANクラスタリング、20点未満のクラスタは破棄されます:
clustering = dbscan(points, 0.05, min_neighbors = 3, min_cluster_size = 20)
```

## 参考文献:

  * Martin Ester, Hans-Peter Kriegel, Jörg Sander, and Xiaowei Xu, *"A density-based algorithm for discovering clusters in large spatial databases with noise"*, KDD-1996, pp. 226–231.
  * Erich Schubert, Jörg Sander, Martin Ester, Hans Peter Kriegel, and Xiaowei Xu, *"DBSCAN Revisited, Revisited: Why and How You Should (Still) Use DBSCAN"*, ACM Transactions on Database Systems, Vol.42(3)3, pp. 1–21, https://doi.org/10.1145/3068335

```
