```julia
mutable struct JumpProblem{iip, P, A, C, J<:Union{Nothing, DiffEqJump.AbstractJumpAggregator}, J2, J3, J4, R} <: SciMLBase.AbstractJumpProblem{P, J<:Union{Nothing, DiffEqJump.AbstractJumpAggregator}}
```

別の問題タイプに関連付けるためのジャンププロセスのコレクションを定義します。

  * [ドキュメントページ](https://jump.sciml.ai/stable/jump_types/)
  * [チュートリアルページ](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)
  * [FAQページ](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/#FAQ)

### コンストラクタ

`JumpProblem`は、ジャンプが関連付けられる別の問題タイプを最初に構築することによって構築できます。たとえば、ジャンプ間で遷移率が一定のジャンププロセスのコレクションをシミュレートするには（[`ConstantRateJump`](@ref)または[`MassActionJump`](@ref)と呼ばれる）、最初に[`DiscreteProblem`](https://docs.sciml.ai/dev/modules/DiffEqDocs/types/discrete_types/)を構築する必要があります。

```julia
prob = DiscreteProblem(u0, p, tspan)
```

ここで、`u0`は初期条件、`p`はパラメータ、`tspan`は時間範囲です。ジャンプをODEのシステムに結び付けたり、明示的な時間依存性を持つ遷移率を持たせたりしたい場合は、ODEの動的部分を定義する`ODEProblem`を代わりに使用します。

`prob`が与えられた場合、ジャンプを次のように定義します。

  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps::JumpSet ; kwargs...)`
  * `JumpProblem(prob, aggregator::AbstractAggregatorAlgorithm, jumps...; kwargs...)`

ここで、`aggregator`は次のジャンプの時間とタイプを計算するための基礎となるアルゴリズムを指定します。たとえば、[`Direct`](@ref)などです。異なる`AbstractJump`タイプのコレクションは、単一の[`JumpSet`](@ref)内またはその後の順次引数として渡すことができます。

### フィールド

  * `prob`: ジャンプを結び付ける問題のタイプ。純粋なジャンププロセスには`DiscreteProblem`を使用し、ODEに結び付けるには`ODEProblem`などを使用します。
  * `aggregator`: `ConstantRateJump`や`MassActionJump`の次のジャンプの時間とタイプを決定する集約アルゴリズム。例として`Direct`があります。
  * `discrete_jump_aggregation`: 選択した集約器に関連付けられた基礎となる状態データ。
  * `jump_callback`: 基礎となる`ConstantRate`および`VariableRate`ジャンプを持つ`CallBackSet`。
  * `variable_jumps`: `VariableRateJump`。
  * `regular_jump`: `RegularJump`。
  * `massaction_jump`: `MassActionJump`。
  * `rng`: 使用する乱数生成器。

## キーワード引数

  * `rng`: 使用する乱数生成器。1.7以降はJuliaの組み込み生成器がデフォルトで、1.7未満ではRandomNumbers.jlの`Xorshifts.Xoroshiro128Star(rand(UInt64))`を使用します。
  * `save_positions=(true,true)`: ジャンプが発生する前後のシステムの状態を保存するかどうかを指定します。
  * `spatial_system`: 空間問題の場合、基礎となる空間構造。
  * `hopping_constants`: 空間問題の場合、空間遷移率係数。

使用例やよくある質問については、DifferentialEquations.jlの[ドキュメント](https://jump.sciml.ai/stable/)の[チュートリアルページ](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)を参照してください。
