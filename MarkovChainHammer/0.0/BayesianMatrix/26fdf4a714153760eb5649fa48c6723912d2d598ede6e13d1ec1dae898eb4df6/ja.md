```
BayesianGenerator(data::Vector{Vector{Int64}}, prior::GeneratorParameterDistributions; dt=1)

ベイズ生成器コンストラクタのアンサンブルバージョンです。ここで、データは整数のベクトルのベクトルであり、各整数のベクトルは単一のアンサンブルメンバーの軌跡です。

# 引数
- `data::Vector{Vector{Int64}}`: BayesianGeneratorオブジェクトを構築するためのデータ。
- `prior::GeneratorParameterDistributions`: BayesianGeneratorオブジェクトのための事前分布。

# キーワード引数
- `dt::Number=1`: 各データポイント間の時間ステップ。

# 戻り値
- `BayesianGenerator`: データと事前分布から構築されたBayesianGeneratorオブジェクト。レートと出口確率の事後分布、ならびに保持時間と出口カウントの予測分布を含みます。
```
