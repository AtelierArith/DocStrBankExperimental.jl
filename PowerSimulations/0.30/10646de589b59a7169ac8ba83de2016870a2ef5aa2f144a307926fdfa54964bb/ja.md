```julia
load_results!(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    count::Int64;
    initial_time,
    variables,
    duals,
    parameters,
    aux_variables,
    expressions,
    store
)

```

シミュレーション結果をメモリに読み込んで、繰り返し読み取るために使用します。これは、ネットワーク接続を介してリモートの場所から結果を読み込む場合や、同じデータを非常に多くの回数読み取る場合に便利です。複数回の呼び出しは、次のルールに従ってキャッシュを増強します。「変数」とは「変数、式など」を意味します：

  * すでにキャッシュされている変数に対して、既にキャッシュされているよりも少ない `count` でリクエストを行っても、キャッシュされた変数の `count` は *減少しません*
  * すでにキャッシュされている変数に対して、既にキャッシュされているよりも大きい `count` でリクエストを行うと、キャッシュされた変数の `count` は *増加します*
  * 新しい変数に対するリクエストは、既存の変数を追い出すことなく満たされます

`count` はすべての変数に対してグローバルであるため、`count` を増やすと、すでにキャッシュされている変数が再読み込みされます。各変数について、各要素は文字列としてエンコードされた名前である必要があります。例えば、`"ActivePowerVariable__ThermalStandard"` のように、またはその構成要素の型を持つタプルのように、`(ActivePowerVariable, ThermalStandard)` のようにします。キャッシュをクリアするには、[`Base.empty!`](@ref) を使用します。

# 引数

  * `count::Int`: 読み込むウィンドウの数。
  * `initial_time::Dates.DateTime` : 読み込む最初のウィンドウの初期時間。デフォルトは最初。
  * `aux_variables::Vector{Union{String, Tuple}}`: 読み込むオプションの補助変数のリスト。
  * `duals::Vector{Union{String, Tuple}}`: 読み込むオプションの双対のリスト。
  * `expressions::Vector{Union{String, Tuple}}`: 読み込むオプションの式のリスト。
  * `parameters::Vector{Union{String, Tuple}}`: 読み込むオプションのパラメータのリスト。
  * `variables::Vector{Union{String, Tuple}}`: 読み込むオプションの変数のリスト。
