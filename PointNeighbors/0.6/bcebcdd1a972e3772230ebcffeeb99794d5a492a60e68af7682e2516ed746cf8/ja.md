```
GridNeighborhoodSearch{NDIMS}(; search_radius = 0.0, n_points = 0,
                              periodic_box = nothing,
                              cell_list = DictionaryCellList{NDIMS}(),
                              update_strategy = nothing)
```

均一な探索半径を持つシンプルなグリッドベースの近傍探索。ドメインは規則的なグリッドに分割されます。各（空でない）グリッドセルについて、そのセル内のポイントのリストが保存されます。有限のドメインをセルの配列で表す代わりに、ハッシュテーブルにセルリストを保存することで、潜在的に無限のドメインを表現します（Juliaの`Dict`データ構造を使用）。これは、セルインデックスタプルでインデックス付けされます。

$$
\left( \left\lfloor \frac{x}{d} \right\rfloor, \left\lfloor \frac{y}{d} \right\rfloor \right) \quad \text{または} \quad
\left( \left\lfloor \frac{x}{d} \right\rfloor, \left\lfloor \frac{y}{d} \right\rfloor, \left\lfloor \frac{z}{d} \right\rfloor \right),
$$

ここで、$x, y, z$は空間座標で、$d$は探索半径です。

位置の周りの探索半径内のポイントを見つけるためには、隣接するセル内のポイントのみが考慮されます。

参照: (Chalela et al., 2021), (Ihmsen et al. 2011, Section 4.4)。

(Ihmsen et al. 2011)とは異なり、ポイントを何らかの方法でソートすることはありません。ソートしないことで、実装が大幅に高速化されます（ただし、並列化は難しくなります）。

# 引数

  * `NDIMS`: 次元数。

# キーワード

  * `search_radius = 0.0`:    固定の探索半径。デフォルトの`0.0`は、                           [`copy_neighborhood_search`](@ref)と一緒に使用するのに便利です。
  * `n_points = 0`:           ポイントの総数。デフォルトの`0`は、                           [`copy_neighborhood_search`](@ref)と一緒に使用するのに便利です。
  * `periodic_box = nothing`: （長方形の）周期的ドメインを使用するには、                           [`PeriodicBox`](@ref)を渡します。
  * `cell_list`:              セルインデックスをセル内のポイントのリストにマッピングするセルリスト。デフォルトでは、                           [`DictionaryCellList`](@ref)が使用されます。
  * `update_strategy = nothing`: `update!`を並列化するための戦略。利用可能なオプションは：

      * `nothing`: 最適な利用可能なオプションを自動的に選択します。
      * [`ParallelUpdate()`](@ref): これはすべてのセルリスト実装で利用できるわけではありません。
      * [`SemiParallelUpdate()`](@ref): これはすべてのセルリスト実装で利用可能で、利用可能な場合はデフォルトです。
      * [`SerialIncrementalUpdate()`](@ref)
      * [`SerialUpdate()`](@ref)

## 参考文献

  * M. Chalela, E. Sillero, L. Pereyra, M.A. Garcia, J.B. Cabral, M. Lares, M. Merchán. "GriSPy: A Python package for fixed-radius nearest neighbors search". In: Astronomy and Computing 34 (2021). [doi: 10.1016/j.ascom.2020.100443](https://doi.org/10.1016/j.ascom.2020.100443)
  * Markus Ihmsen, Nadir Akinci, Markus Becker, Matthias Teschner. "A Parallel SPH Implementation on Multi-Core CPUs". In: Computer Graphics Forum 30.1 (2011), pages 99–112. [doi: 10.1111/J.1467-8659.2010.01832.X](https://doi.org/10.1111/J.1467-8659.2010.01832.X)

```
