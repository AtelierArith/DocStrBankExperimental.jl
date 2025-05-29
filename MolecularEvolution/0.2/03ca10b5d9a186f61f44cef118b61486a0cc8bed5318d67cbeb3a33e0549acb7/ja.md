```
metropolis_sample(
    update!::AbstractUpdate,
    initial_tree::FelNode,
    models,
    num_of_samples;
    partition_list = 1:length(initial_tree.message),
    burn_in = 1000,
    sample_interval = 10,
    collect_LLs = false,
    collect_models = false,
    midpoint_rooting = false,
    ladderize = false,
)
```

カスタム `update!` 関数を使用して、事後分布から木のトポロジーをサンプリングします。

# 引数

  * `update!`: (tree::FelNode, models) を受け取り、`tree` と `models` を更新する呼び出し可能な関数。`update!` の1回の呼び出しは、メトロポリスアルゴリズムの1回の反復に対応します。
  * `initial_tree`: 尤度計算のためにデータで葉が populated された初期の木のトポロジー。
  * `models`: ブランチモデルのリスト。
  * `num_of_samples`: 事後から引き出される木のサンプル数。
  * `partition_list`: (例: 1:3 または [1,3,5]) 実行するパーティションを選択できます（ただし、すべてのパーティションでサンプリングしたいと思うでしょう。デフォルトオプションです）。
  * `burn_in`: マルコフ連鎖の開始時に破棄されるサンプルの数。
  * `sample_interval`: 基本のマルコフ連鎖におけるサンプル間の距離（サンプルの相関を減らすため）。
  * `collect_LLs`: 関数が木の対数尤度を返すべきかどうかを指定します。
  * `collect_models`: 関数がモデルを返すべきかどうかを指定します。
  * `midpoint_rooting`: 引き出されたサンプルがミッドポイントで再根付けされるべきかどうかを指定します（重要！平衡状態から始まる時間可逆ブランチモデルにのみ使用するべきです）。

!!! note
    初期の木の葉はデータで populated されている必要があり、この関数を呼び出す前に felsenstein! を初期の木に対して呼び出す必要があります。


# 戻り値

  * `samples`: 事後から引き出された木。浅い木のコピーを返し、felsenstein! などを実行する前に再度 populated する必要があります。
  * `sample_LLs`: 木の関連する対数尤度（オプション）。
  * `sample_models`: 事後から引き出されたモデル（オプション）。モデルは `collapse_models` を使用してそのパラメータに圧縮できます。
