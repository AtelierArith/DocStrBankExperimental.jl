```
Scenario(
  model::Model,
  tspan;
  measurements::Vector{AbstractMeasurementPoint}=AbstractMeasurementPoint[],
  observables::Union{Nothing,Vector{Symbol}}=nothing,
  parameters::AbstractVector{<:Pair{Symbol,<:Real}} = Pair{Symbol,Float64}[],
  events_active::Union{Nothing, Vector{Pair{Symbol,Bool}}} = Pair{Symbol,Bool}[],
  events_save::Union{Tuple,Vector{Pair{Symbol, Tuple{Bool, Bool}}}} = (true,true),
  saveat::Union{Nothing,AbstractVector} = nothing,

  save_scope::Bool = true,
)
```

シミュレーションシナリオのタイプ [`Scenario`](@ref) を構築します。

例: `Scenario(model, (0., 200.))`

引数:

  * `model` : タイプ [`Model`](@ref) のモデル
  * `tspan` : ODE問題の時間範囲
  * `measurements` : 測定値の `Vector`。デフォルトは空の `Vector{AbstractMeasurementPoint}`
  * `observables` : 出力の可観測量の名前。デフォルトのモデルの値を上書きします。デフォルトは `nothing`
  * `tags` :
  * `group` :
  * `parameters` : パラメータの名前と値を含む `Pair` の `Vector`。デフォルトのモデルの値を上書きします。デフォルトは空のベクター。
  * `events_active` : イベントの名前と真偽値を含む `Pair` の `Vector`。デフォルトのモデルの値を上書きします。デフォルトは空の `Vector{Pair}`
  * `events_save` : イベントの前後に解を保存するかどうかを示す `Tuple` または `Vector{Tuple}`。すべてのイベントに対してデフォルトは `(true,true)`
  * `saveat` : 解を保存すべき時間点。デフォルトの `nothing` 値は、ソルバーによって到達した時間点で解を保存することを示します
  * `save_scope` : スコープを解と一緒に保存するべきか。デフォルトは `true`
