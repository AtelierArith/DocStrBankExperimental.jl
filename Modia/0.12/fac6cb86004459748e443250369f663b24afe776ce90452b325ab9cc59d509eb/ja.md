```
simulationModel = InstantiatedModel{FloatType,TimeType}(
        modelModule, modelName, getDerivatives!, equationInfo, x_startValues,
        parameters, timeName, w_invariant_names;
        vSolvedWithInitValuesAndUnit::OrderedDict{String,Any}(),
        vEliminated::Vector{Int}=Int[],
        vProperty::Vector{Int}=Int[],
        var_name::Function = v->nothing)
```

# 引数

  * `modelModule`: `@instantiateModel` が呼び出されるモジュール（`Core.eval(modelModule, ...)` に使用され、ユーザーの環境での式の評価を行います）。
  * `modelName::String`: モデルの名前
  * `getDerivatives::Function`: モデル方程式を評価するために使用される関数で、通常は [`Modia.generate_getDerivatives!`] で生成されます。
  * `equationInfo::Modia.EquationInfo`: 状態と方程式に関する情報。
  * `x_startValues`:: 非推奨（もはや使用されていません）。
  * `parameters`: パラメータと初期/開始値を定義する (key, value) ペアの階層型 NamedTuple。
  * `timeName`: 時間の名前（シンボルとして）
  * `w_invariant_names`: 変数名のベクトル（シンボルまたは Expr のベクトルとして）
