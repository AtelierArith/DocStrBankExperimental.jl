# サンプルタイプとコンストラクタ

Stanmodelにおけるmethod=Sample()の設定。

### メソッド

```julia
Sample(;
  num_samples=1000,
  num_warmup=1000,
  save_warmup=false,
  thin=1,
  adapt=CmdStan.Adapt(),
  algorithm=SamplingAlgorithm()
)
```

### オプション引数

```julia
* `num_samples::Int64`          : サンプリング反復の数 ( >= 0 )
* `num_warmup::Int64`           : ウォームアップ反復の数 ( >= 0 )
* `save_warmup::Bool`           : 出力にウォームアップサンプルを含める
* `thin::Int64`                 : 保存されたサンプル間の期間
* `adapt::Adapt`                : ウォームアップ適応設定
* `algorithm::SamplingAlgorithm`: サンプリングアルゴリズム

```

### 関連ヘルプ

```julia
?Stanmodel                      : StanModelを作成する
?Adapt
?SamplingAlgorithm
```
