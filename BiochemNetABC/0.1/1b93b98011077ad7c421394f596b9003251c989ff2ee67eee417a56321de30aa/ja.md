```
rf_abc_model_choice(abc_trainset;
                    k::Int = N_ref, distance_func::Function = (x,y) -> 1, 
                    hyperparameters_range::Dict)
```

既にシミュレーションされたデータセットを使用して、ランダムフォレスト近似ベイズ計算モデル選択メソッドを実行します。

必須の引数は次のとおりです：

  * `abc_trainset`: $abc_model_choice_dataset$ でシミュレーションされたデータセット

オプションの引数は次のとおりです：

  * `hyperparameters_range`: ランダムフォレストのクロスバリデーションフィットのためのハイパーパラメータ範囲値を持つ辞書（デフォルト: `Dict(:n_estimators => [200], :min_samples_leaf => [1], :min_samples_split => [2])`）。ハイパーパラメータ名については、scikit-learnのRandomForestClassifierのドキュメントを参照してください。

結果は、次のフィールドを持つ `RandomForestABC` オブジェクトです：

  * `reference_table` アルゴリズムの参照テーブルに対応するAbcModelChoiceDataset、
  * `clf` ランダムフォレスト分類器（scikit-learnのPyObject）、
  * `summary_stats_observations` 観測の要約統計、
  * `estim_model` RF-ABCメソッドで推測された観測の基礎モデルです。
