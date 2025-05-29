```julia
mutable struct JumpProblem{iip, P, A, C, J<:Union{Nothing, JumpProcesses.AbstractJumpAggregator}, J2, J3, J4, R, K} <: SciMLBase.AbstractJumpProblem{P, J<:Union{Nothing, JumpProcesses.AbstractJumpAggregator}}
```

別の問題タイプに関連付けるためのジャンププロセスのコレクションを定義します。

  * [ドキュメンテーションページ](https://docs.sciml.ai/JumpProcesses/stable/jump_types/)
  * [チュートリアルページ](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)
  * [FAQページ](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/#FAQ)

### コンストラクタ

`JumpProblem`は、ジャンプが関連付けられる別の問題タイプを最初に構築することによって構築できます。たとえば、ジャンプ間で遷移率が一定のジャンププロセスのコレクションをシミュレートするには（[`ConstantRateJump`](@ref)または[`MassActionJump`](@ref)と呼ばれる）、最初に[`DiscreteProblem`](https://docs.sciml.ai/DiffEqDocs/stable/types/discrete_types/)を構築する必要があります。

```julia
prob = DiscreteProblem(u0, p, tspan)
```

ここで、`u0`は初期条件、`p`はパラメータ、`tspan`は時間範囲です。ジャンプをODEのシステムに結び付けたり、明示的な時間依存性を持つ遷移率を持たせたりしたい場合は、ODEの動的部分を定義する`ODEProblem`を使用します。

`prob`が与えられた場合、ジャンプは次のように定義します。

  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps::JumpSet ; kwargs...)`
  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps...; kwargs...)`

ここで、`aggregator`は次のジャンプの時間とタイプを計算するための基礎となるアルゴリズムを指定します。たとえば、[`Direct`](@ref)などです。異なる`AbstractJump`タイプのコレクションは、単一の[`JumpSet`](@ref)内またはその後の順次引数として渡すことができます。

### フィールド

  * `prob`: ジャンプを結び付ける問題のタイプ。純粋なジャンププロセスには`DiscreteProblem`を使用し、ODEに結び付けるには`ODEProblem`などを使用します。
  * `aggregator`: `ConstantRateJump`や`MassActionJump`の次のジャンプの時間とタイプを決定する集約アルゴリズム。例として`Direct`があります。
  * `discrete_jump_aggregation`: 選択した集約器に関連付けられた基礎状態データ。
  * `jump_callback`: 基礎となる`ConstantRate`および`VariableRate`ジャンプを持つ`CallBackSet`。
  * `variable_jumps`: `VariableRateJump`。
  * `regular_jump`: `RegularJump`。
  * `massaction_jump`: `MassActionJump`。
  * `rng`: 使用する乱数生成器。
  * `kwargs`: solve呼び出しに渡すkwargs。

## キーワード引数

  * `rng`: 使用する乱数生成器。デフォルトはJuliaの組み込みジェネレーターです。
  * `save_positions=(true,true)`: ジャンプが発生する前後のシステムの状態を保存するかどうかを指定します。
  * `spatial_system`: 空間問題の場合、基礎となる空間構造。
  * `hopping_constants`: 空間問題の場合、空間遷移率係数。
  * `use_vrj_bounds = true`: `Coevolve`のようなサポート集約器を持つ制約付き`VariableRateJump`の処理を無効にするにはfalseに設定します。それらは連続統合インターフェースを介して処理され、一般的な`VariableRateJump`のように扱われます。

使用例やよくある質問については、DifferentialEquations.jlの[チュートリアルページ](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)を参照してください。
