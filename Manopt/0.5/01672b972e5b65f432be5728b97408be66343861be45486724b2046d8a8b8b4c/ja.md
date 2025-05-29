```
ArmijoLinesearch(; kwargs...)
ArmijoLinesearch(M::AbstractManifold; kwargs...)
```

Armijoラインサーチを実行するステップサイズを指定します。関数 $f:\mathcal M→ℝ$ とそのリーマン勾配 $\operatorname{grad}f: \mathcal M→T\mathcal M$、現在の点 $p∈\mathcal M$ および探索方向 $X∈T_{p}\mathcal M$ が与えられたとき。

その後、ステップサイズ $s$ は、次の条件が満たされるまで初期ステップサイズ $s$ を減少させることによって見つけられます。

$$
f(\operatorname{retr}_p(sX)) ≤ f(p) - τs ⟨ X, \operatorname{grad}f(p) ⟩_p
$$

ここで、十分な減少値 $τ ∈ (0,1)$ です。

もう少し楽観的に言えば、もし $s$ がすでにこの条件を満たしている場合、最初の探索が行われ、**与えられた** $s$ を増加させて、初めてこのステップが成り立たないまで続けます。

全体として、*十分な減少*を提供するステップサイズを探します。詳細については、[Boumal:2023; p. 58](@cite) を参照してください。

# キーワード引数

  * `additional_decrease_condition=(M, p) -> true`: 減少ループでステップサイズを受け入れるために満たす必要がある追加の基準を指定します
  * `additional_increase_condition::IF=(M, p) -> true`: (初期)増加ループでステップサイズを受け入れるために満たす必要がある追加の基準を指定します
  * `candidate_point=allocate_result(M, rand)`: 候補点のメモリとして使用する点を指定します。
  * `contraction_factor=0.95`: 減少ステップで $s$ を更新する方法
  * `initial_stepsize=1.0``: 初期ステップサイズを指定します
  * `initial_guess=`[`armijo_initial_guess`](@ref): この関数に基づいてラインサーチの初期ステップサイズを計算します。必要な関数は `(p,s,k,l) -> α` で、[`AbstractManoptProblem`](@ref) `p`、[`AbstractManoptSolverState`](@ref) `s`、現在の反復 `k` および最後のステップサイズ `l` に基づいて初期ステップサイズ $α$ を計算します。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関する[セクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `stop_when_stepsize_less=0.0`: セーフガード、減少ステップがこの（非負の）制約を下回ったときに停止します。
  * `stop_when_stepsize_exceeds=max_stepsize(M)`: 初期増加時にあまり長いステップサイズを選択しないためのセーフガード
  * `stop_increasing_at_step=100`: このステップ数後に初期増加ループを停止します。最初に増加しないようにするには `0` に設定します
  * `stop_decreasing_at_step=1000`: 実行するArmijo減少/テストの最大数
  * `sufficient_decrease=0.1`: 十分な減少パラメータ $τ$

停止のセーフガードには、`debug=` に `:Messages` を渡すことで、これらが発生したときに `@info` メッセージを見ることができます。

!!! info
    この関数は [`ArmijoLinesearchStepsize`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値については、このファクトリは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。


```
