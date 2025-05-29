```
runsampler(data,
options = MCMCOptionsList(),
params = PriorHyperparamsList();
verbose = true) -> MCMCResult
```

データに対してMCMCサンプラーを実行します。

# 引数

  * `data::MCMCData`: 距離行列を含みます。
  * `options::MCMCOptionsList`: イテレーション数、バーンインなどを含みます。
  * `params::PriorHyperparamsList`: モデルのための事前ハイパーパラメータを含みます。
  * `verbose::Bool`: falseの場合、すべての情報メッセージと進行状況バーを無効にします。

# 戻り値

MCMCサンプル、収束診断、および要約統計を含む`MCMCResult`型の構造体。

# 参照

[`MCMCData`](@ref), [`MCMCOptionsList`](@ref), [`fitprior`](@ref), [`PriorHyperparamsList`](@ref), [`MCMCResult`](@ref).
