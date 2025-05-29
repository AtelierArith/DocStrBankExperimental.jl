```
function optimize_by_walking_CNN!(cnn_jump::JuMP.Model, input; iterations=10, samples_per_iter=5, timelimit=1.0, tolerance=1.0)
```

与えられた畳み込みニューラルネットワークのJuMP定式化に対して、完全なリラクシングウォークアルゴリズムを実行します。詳細については、Tong et al. (2024)を参照してください。

# パラメータ

  * `cnn_jump`: CNN定式化を含む`JuMP`モデル。
  * `input`: CNNへの例示的な入力。入力の次元を抽出するために使用されます。

# オプションのパラメータ

  * `iterations`: 線形リラクゼーションからの新しいスタートの数（バイナリ変数が固定されていない）
  * `samples_per_iter`: イテレーションごとの成功したサンプルの最大数
  * `timelimit`: LPリラクゼーションの解決のための時間制限
  * `tolerance`: 新しいサンプルが以前のサンプルとどれだけ異なる必要があるか
