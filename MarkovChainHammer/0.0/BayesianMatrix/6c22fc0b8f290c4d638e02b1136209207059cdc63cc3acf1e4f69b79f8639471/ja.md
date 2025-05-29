```
BayesianGenerator(parameters::NamedTuple)
```

NamedTupleのパラメータからBayesianGeneratorオブジェクトを構築します。

# 引数

  * `parameters::NamedTuple`: BayesianGeneratorオブジェクトのためのパラメータを含むNamedTuple。`prior`、`posterior`、`predictive`のフィールドを含む必要があり、それぞれのフィールドは対応する分布のためのパラメータを含むNamedTupleでなければなりません。

# 戻り値

  * `BayesianGenerator`: パラメータから構築されたBayesianGeneratorオブジェクト。レートと退出確率の事後分布、および保持時間と退出カウントの予測分布を含みます。
