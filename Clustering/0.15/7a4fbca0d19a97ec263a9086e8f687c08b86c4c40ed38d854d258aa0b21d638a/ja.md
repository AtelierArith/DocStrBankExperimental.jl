```
mcl(adj::AbstractMatrix; [kwargs...]) -> MCLResult
```

$$
n×n
$$

隣接行列 `adj` を使用して MCL (マルコフクラスタリングアルゴリズム) クラスタリングを実行します。

# 引数

MCL アルゴリズムを制御するためのキーワード引数：

  * `add_loops::Bool` (デフォルトで有効): ノードから自身への重み 1.0 のエッジをグラフに追加するかどうか
  * `expansion::Number` (デフォルトは 2): MCL *拡張* 定数
  * `inflation::Number` (デフォルトは 2): MCL *膨張* 定数
  * `save_final_matrix::Bool` (デフォルトで無効): 結果の `mcl_adj` フィールドに最終的な平衡状態を保存するかどうか; メソッドが収束しない場合に有用な診断を提供する可能性があります
  * `prune_tol::Number`: プルーニング閾値
  * `display`, `maxiter`, `tol`: [共通オプション](@ref common_options)を参照

# 参考文献

> Stijn van Dongen, *"Graph clustering by flow simulation"*, 2001


> [オリジナルの MCL 実装](http://micans.org/mcl).

