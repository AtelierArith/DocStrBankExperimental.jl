```
Rulseset <: AbstractRuleset

Ruleset(rules...; kw...)
Ruleset(rules, settings)
```

`Rule`のシーケンスと境界処理や最適化のようなシミュレーションの詳細を保持するためのコンテナです。ルールは渡された順序で実行されます。つまり、`Ruleset(rule1, rule2, rule3)`のようになります。

# キーワード

  * `proc`: シミュレーションを実行するハードウェアを指定するための[`Processor`](@ref)、例えば[`SingleCPU`](@ref)、[`ThreadedCPU`](@ref)または[`CuGPU`](@ref)がKernelAbstractions.jlとCUDA GPUが利用可能な場合に使用されます。
  * `opt`: [`SparseOpt`](@ref)のような最適化を指定するための[`PerformanceOpt`](@ref)。デフォルトは[`NoOpt`](@ref)です。
  * `boundary`: グリッドエッジの境界に対して何をするか。オプションは`Remove()`または`Wrap()`で、デフォルトは[`Remove`](@ref)です。
  * `cellsize`: セルのサイズ。
  * `timestep`: 一部のルールに必要な固定タイムステップ。例：`Month(1)`または`1u"s"`。
