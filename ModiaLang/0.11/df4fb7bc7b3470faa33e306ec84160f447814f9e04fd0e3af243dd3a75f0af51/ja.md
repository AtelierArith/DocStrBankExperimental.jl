```
simulationModel = SimulationModel{FloatType,TimeType}(
        modelModule, modelName, getDerivatives!, equationInfo, x_startValues,
        parameters, variableNames;
        vSolvedWithInitValuesAndUnit::OrderedDict{String,Any}(),
        vEliminated::Vector{Int}=Int[],
        vProperty::Vector{Int}=Int[],
        var_name::Function = v->nothing)
```

# 引数

  * `modelModule`: `@instantiateModel` が呼び出されるモジュール（`Core.eval(modelModule, ...)` に使用され、ユーザーの環境での式の評価を行います）。
  * `modelName::String`: モデルの名前
  * `getDerivatives::Function`: モデル方程式を評価するために使用される関数で、通常は [`ModiaLang.generate_getDerivatives!`] で生成されます。
  * `equationInfo::ModiaBase.EquationInfo`: 状態と方程式に関する情報。
  * `x_startValues`:: 非推奨（もはや使用されていません）。
  * `parameters`: パラメータと初期/開始値を定義する (key, value) ペアの階層型 NamedTuple。
  * variableNames: 変数名のベクター。名前はシンボルまたは文字列であることができます。
