```
item_information_curve(model, item, response)
item_information_curve(model, item)
```

`item`の`response`に対する項目情報曲線のプロットを作成します。

`response`が省略された場合、デフォルトのプロット動作は`model`に依存します：

  * `response_type(model) == Dichotomous`の場合、総項目情報曲線がプロットされます。
  * `response_type(model) <: Union{Nominal, Ordinal}`の場合、すべてのカテゴリ情報曲線がプロットされます。

# プロット属性

## 一般

  * `color`: 項目情報曲線の色。
  * `uncertainty_color`: 表示される不確実性情報の色。不確実性区間を持つプロットでは、これは信頼帯の色です。サンプルベースの不確実性情報を持つプロットでは、これはサンプルの線の色です。
  * `theta`: 項目情報曲線をプロットするための`theta`の値。デフォルト: -3.0:0.01:3.0。

## 特定

### `SamplingEstimate`を持つモデル

  * `samples`: プロットするサンプルの数。デフォルト: `1000`
  * `uncertainty_type`: 推定の不確実性の表示方法を変更します。`uncertainty_type = :samples`の場合、MCMC推定からの反復がプロットされます。`uncertainty_type = :interval`の場合、不確実性区間がプロットされます。デフォルト: `:samples`
  * `quantiles`: 不確実性区間の下限および上限の分位数。デフォルト: `(0.1, 0.9)`
  * `aggregate_fun`: MCMCサンプルを集約する関数。提供された関数はベクトルを入力として受け取り、スカラー値を出力する必要があります。`aggregate_fun = nothing`の場合、集約はプロットされません。デフォルト: mean
