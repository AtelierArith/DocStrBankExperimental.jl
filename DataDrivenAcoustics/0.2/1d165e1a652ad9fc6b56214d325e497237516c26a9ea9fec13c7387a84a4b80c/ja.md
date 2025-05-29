```julia
ModelFit!(
    r,
    inilearnrate,
    trainloss,
    dataloss,
    ratioₜ,
    seed,
    maxepoch,
    ncount,
    minlearnrate,
    reducedlearnrate,
    showloss
)

```

データ駆動型物理ベースの伝播モデルをトレーニングします。

  * `ini_lr`: 初期学習率
  * `trainloss`: トレーニングおよびモデル更新に使用される損失関数
  * `dataloss`: 早期停止のためのベンチマーク検証エラーを計算するデータ損失関数
  * `ratioₜ`: データ分割比 = トレーニングデータの数 / (トレーニングデータの数 + 検証データの数)
  * `seed`を`true`に設定すると、ランダムデータ選択順序のシードが設定されます
  * `maxepoch`: 許可される最大トレーニングエポック数
  * `ncount`: 学習率を減少させる前の最大試行回数
  * 学習率が`minlearnrate`より小さくなるとモデルのトレーニングが終了します
  * `ncount`に達すると、学習率は`reducedlearnrate`によって減少します
  * `showloss`をtrueに設定すると、モデルのトレーニングプロセス中にトレーニングおよび検証エラーが表示されます（検証エラーが歴史的に最良の場合）。
