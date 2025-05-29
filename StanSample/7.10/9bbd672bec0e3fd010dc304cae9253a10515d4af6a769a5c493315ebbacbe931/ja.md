StanSummaryを作成する

```julia
describe(model, params; round_estimates, digits)

```

## 必須の位置引数

```julia
* `model::SampleModel` # ドローを作成するために使用されるSampleModel
```

## オプションの位置引数

```julia
* `params` # 含めるシンボルまたは文字列のベクター
```

## キーワード引数

```julia
* `round_estimates = true` #
* `digits = 3` # 小数点以下の桁数
```

## 戻り値

StanSummaryオブジェクト。
