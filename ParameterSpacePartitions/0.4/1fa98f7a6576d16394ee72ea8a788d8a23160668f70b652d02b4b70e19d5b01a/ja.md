```
estimate_volume(
    model, 
    p_fun, 
    points, 
    target, 
    bounds,  
    args...;
    n_sim = 10_000,
    kwargs...
)
```

楕円体を用いた領域の体積を推定し、ヒットまたはミスのバイアス調整を行います。

# 引数

  * `model`: パラメータのベクトルに基づいて予測を返すモデル関数
  * `p_fun`: 定性的データパターンを評価する関数
  * `points`: p x n の行列で、p はパラメータの数、n はサンプルの数
  * `target`: `points` に関連付けられたターゲットパターン
  * `bounds`: 各次元の (下限, 上限) を表すタプルのベクトル
  * `args...`: `model` と `p_fun` に渡される引数

# キーワード

  * `n_sim=10_000`: ヒットまたはミスのバイアス調整のためのサンプル数
  * `kwargs...`: `model` または `p_fun` に渡される追加のキーワード引数
