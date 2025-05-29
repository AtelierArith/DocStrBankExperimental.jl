```
item_characteristic_curve(model, item, response)
item_characteristic_curve(model, item)
```

`item`の`response`に対する項特性曲線のプロットを作成します。

項特性曲線は、人物の能力θに対する`item`の`response`の確率をプロットします。

`response`が省略されると、デフォルトのプロット動作は`model`に依存します：

  * `response_type(model) == Dichotomous`のモデルの場合、response = 1の項特性曲線がプロットされます。すなわち、正しい応答の確率です。
  * `response_type(model) <: Union{Nominal, Ordinal}`のモデルの場合、すべてのカテゴリ特性曲線がプロットされます。

# プロット属性

## 一般

  * `color`: 項特性曲線の色。
  * `uncertainty_color`: 表示される不確実性情報の色。不確実性区間を持つプロットの場合、これは信頼帯の色です。サンプルベースの不確実性情報を持つプロットの場合、これはサンプルの線の色です。
  * `theta`: 項特性曲線をプロットするための`theta`の値。デフォルト: -3.0:0.01:3.0。
  * `show_data`: プロットに観測データをオーバーレイします。能力推定値は`bins`に従って集約されます。`estimation_type(model) == SamplingEstimate`のモデルの場合、ビン分けには能力推定値の事後平均が使用されます。デフォルト: false。
  * `bins`: 観測データのビンの数。デフォルト: 6。

## 特定

### `SamplingEstimate`を持つモデル

  * `samples`: プロットするサンプルの数。デフォルト: `1000`
  * `uncertainty_type`: 推定の不確実性の表示方法を変更します。`uncertainty_type = :samples`の場合、MCMC推定からの反復がプロットされます。`uncertainty_type = :interval`の場合、不確実性区間がプロットされます。デフォルト: `:samples`
  * `quantiles`: 不確実性区間の下限および上限の分位数。デフォルト: `(0.1, 0.9)`
  * `aggregate_fun`: MCMCサンプルを集約する関数。提供された関数はベクトルを入力として受け取り、スカラー値を出力する必要があります。`aggregate_fun = nothing`の場合、集約はプロットされません。デフォルト: mean

```
