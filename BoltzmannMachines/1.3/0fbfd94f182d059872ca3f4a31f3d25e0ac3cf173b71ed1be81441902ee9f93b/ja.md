RBM層をDBMでトレーニングするためのパラメータを指定します。

# オプションのキーワード引数:

  * オプションのキーワード引数 `rbmtype`、`nhidden`、`epochs`、`learningrate`/`learningrates`、`sdlearningrate`/`sdlearningrates`、`categories`、`batchsize`、`pcd`、`cdsteps`、`startrbm` および `optimizer`/`optimizers` は `fitrbm` に渡されます。詳細な説明については、そこを参照してください。`learningrate` または `epochs` に負の値が指定された場合、これは対応するデフォルト値を使用することを示します（`stackrbms` の呼び出しによって定義されたパラメータ）。
  * `monitoring`: `fitrbm` と同様ですが、第三引数として `DataDict` を取ることができます（関数 `stackrbms` とその引数 `monitoringdata` を参照してください）。
  * `nvisible`: RBMの可視ユニットの数。パーティショニングにのみ関連します。このパラメータは、できるだけ `stackrbms` によって導出されます。パーティションされた最初の層を持つ `MultimodalDBM` の場合、入力層のすべてのパーティションに対して、可視ノードの数を指定する必要がありますが、最大で1つのパーティションを除きます。
