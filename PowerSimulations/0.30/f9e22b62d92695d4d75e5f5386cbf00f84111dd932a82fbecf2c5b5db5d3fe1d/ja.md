```julia
load_results!(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.EmulationModelSimulationResults};
    aux_variables,
    duals,
    expressions,
    parameters,
    variables
)

```

シミュレーション結果をメモリに読み込んで、繰り返し読み取れるようにします。これは、ネットワーク接続を介してリモートの場所から結果を読み込む際に便利です。

各変数/パラメータ/双対などについて、各要素は文字列としてエンコードされた名前である必要があります。例えば、`"ActivePowerVariable__ThermalStandard"`や、その構成要素の型を持つタプル、例えば`(ActivePowerVariable, ThermalStandard)`のようにします。

# 引数

  * `aux_variables::Vector{Union{String, Tuple}}`: 読み込むオプションの補助変数のリスト。
  * `duals::Vector{Union{String, Tuple}}`: 読み込むオプションの双対のリスト。
  * `expressions::Vector{Union{String, Tuple}}`: 読み込むオプションの式のリスト。
  * `parameters::Vector{Union{String, Tuple}}`: 読み込むオプションのパラメータのリスト。
  * `variables::Vector{Union{String, Tuple}}`: 読み込むオプションの変数のリスト。
