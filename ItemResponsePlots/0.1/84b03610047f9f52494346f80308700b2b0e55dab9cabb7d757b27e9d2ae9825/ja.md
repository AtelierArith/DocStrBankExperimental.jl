```
information_plot(model)
information_plot(model, items)
```

`model`のテスト情報のプロットを作成します。

`items`が指定されている場合、テスト情報は`items`のみを含むサブテストに従ってプロットされます。`items`が省略された場合、テスト情報は`model`に含まれるすべてのアイテムについてプロットされます。

# プロット属性

## 一般

  * `color`: 情報プロットの色。
  * `uncertainty_color`: 表示される不確実性情報の色。不確実性区間を持つプロットの場合、これは信頼帯の色です。サンプルベースの不確実性情報を持つプロットの場合、これはサンプルの線の色です。
  * `theta`: 情報をプロットするための`theta`の値。デフォルト: -3.0:0.01:3.0。
  * `scoring_function`: 情報に適用されるスコアリング関数。

## 特定

### `SamplingEstimate`を持つモデル

  * `samples`: プロットするサンプルの数。デフォルト: 1000。
  * `uncertainty_type`: 推定の不確実性が表示される方法を変更します。`uncertainty_type = :samples`の場合、MCMC推定からの反復がプロットされます。`uncertainty_type = :interval`の場合、不確実性区間がプロットされます。デフォルト: `:samples`
  * `quantiles`: 不確実性区間の下限および上限の分位数。デフォルト: `(0.1, 0.9)`
  * `aggregate_fun`: MCMCサンプルを集約する関数。提供された関数はベクトルを入力として受け取り、スカラー値を出力する必要があります。`aggregate_fun = nothing`の場合、集約はプロットされません。デフォルト: mean
