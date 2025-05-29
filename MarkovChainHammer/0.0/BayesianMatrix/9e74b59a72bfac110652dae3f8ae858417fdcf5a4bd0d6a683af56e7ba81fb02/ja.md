```
BayesianGenerator(data, prior::GeneratorParameterDistributions; dt=1)
```

データと事前分布からBayesianGeneratorオブジェクトを構築します。

# 引数

  * `data::Vector{Int}`: BayesianGeneratorオブジェクトを構築するためのデータ。
  * `prior::GeneratorParameterDistributions`: BayesianGeneratorオブジェクトのための事前分布。

# キーワード引数

  * `dt::Number=1`: 各データポイント間の時間ステップ。

# 戻り値

  * `BayesianGenerator`: データと事前分布から構築されたBayesianGeneratorオブジェクト。レートと退出確率の事後分布、ならびに保持時間と退出カウントの予測分布を含みます。
