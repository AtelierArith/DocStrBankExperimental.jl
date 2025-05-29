```
Base.run(sim_def::SimulationDef{T}, 
        models::Union{Vector{M}, AbstractModel}, 
        samplesize::Int;
        ntimesteps::Int=typemax(Int), 
        trials_output_filename::Union{Nothing, AbstractString}=nothing, 
        results_output_dir::Union{Nothing, AbstractString}=nothing, 
        pre_trial_func::Union{Nothing, Function}=nothing, 
        post_trial_func::Union{Nothing, Function}=nothing,
        scenario_func::Union{Nothing, Function}=nothing,
        scenario_placement::ScenarioLoopPlacement=OUTER,
        scenario_args=nothing,
        results_in_memory::Bool=true) where {T <: AbstractSimulationData, M <: AbstractModel}
```

シミュレーション定義 `sim_def` を `models` に対して `samplesize` サンプルで実行します。

オプションとして、指定された場合は `ntimesteps` のために `models` を実行します。指定されていない場合は、最大定義時間期間まで実行されます。試行データは、実行するモデルの一部のみの場合でも、すべての関連モデルに適用されることに注意してください。

提供された場合、生成された試行と結果は、それぞれ指定された `trials_output_filename` と `results_output_dir` に保存されます。`results_in_memory` が false に設定されている場合、結果はメモリからクリアされ、`results_output_dir` にのみ保存されます。

`pre_trial_func` または `post_trial_func` が定義されている場合、指定された関数は試行を実行する直前または直後（それぞれ）に呼び出されます。関数は次のシグネチャを持つ必要があります：

```
fn(sim_inst::SimulationInstance, trialnum::Int, ntimesteps::Int, tup::Tuple)
```

ここで `tup` は、すべてのシナリオ値ベクトルの直積の1要素を表すシナリオ引数のタプルです。シミュレーションループが一部のモデルのみを実行する場合、残りの実行は `pre_trial_func` または `post_trial_func` を使用して処理できます。

提供された場合、`scenario_args` は `Vector{Pair}` でなければならず、各 `Pair` はシンボルと `scenario_func` にとって意味のある任意の値の `Vector` です。`scenario_func` は次のシグネチャを持つ必要があります：

```
scenario_func(sim_inst::SimulationInstance, tup::Tuple)
```

デフォルトでは、シナリオループはシミュレーションループを囲みますが、`scenario_placement=INNER` を指定することでシミュレーションループ内にシナリオループを配置できます。`INNER` が指定されると、`pre_trial_func` の後に `scenario_func` が呼び出されますが、モデルが実行される前に呼び出されます。

元の `SimulationDef` のコピーと、試行に関する変更された情報、モデルリストおよび結果情報を含む `SimulationInstance` 型を返します。
