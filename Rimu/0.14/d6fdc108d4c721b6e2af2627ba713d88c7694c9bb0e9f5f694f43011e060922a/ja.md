```
PostStepStrategy
```

`PostStepStrategy`のサブタイプは、FCIQMCステップが終了した後に単一の状態に対して任意の計算を実行し、その結果を報告するために使用できます。

# 実装された戦略:

  * [`ProjectedEnergy`](@ref)
  * [`Projector`](@ref)
  * [`SignCoherence`](@ref)
  * [`WalkerLoneliness`](@ref)
  * [`Timer`](@ref)

注意: 複数の戦略のタプルを[`ProjectorMonteCarloProblem`](@ref)に渡すことができます。その場合、すべての報告された列名は異なる必要があります。

# インターフェース:

この型のサブタイプは、[`post_step_action(::PostStepStrategy, ::SingleState, step::Int)`](@ref)を実装しなければなりません。
