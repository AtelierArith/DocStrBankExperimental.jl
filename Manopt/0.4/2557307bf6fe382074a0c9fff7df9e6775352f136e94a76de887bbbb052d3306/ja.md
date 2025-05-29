```
ConjugateGradientState <: AbstractGradientSolverState
```

コンjugate gradient descentアルゴリズムのオプションを指定します。このアルゴリズムは[`DefaultManoptProblem`]を解決します。

# フィールド

  * `p`:                       現在の反復点、マニフォールド上の点
  * `X`:                       現在の勾配、$ξ$または$X_k$としても知られ、$k$番目のステップの勾配を表します。
  * `δ`:                       現在の降下方向、接ベクトルでもあります
  * `β`:                       現在の更新係数ルール、参照してください。
  * `coefficient`:             ([`ConjugateDescentCoefficient`](@ref)`()`) 新しい`β`を決定するための[`DirectionUpdateRule`](@ref)関数
  * `stepsize`:                ([`default_stepsize`](@ref)`(M, ConjugateGradientDescentState; retraction_method=retraction_method)`) [`Stepsize`](@ref)関数
  * `stop`:                    ([`StopAfterIteration`](@ref)`(500) |`[`StopWhenGradientNormLess`](@ref)`(1e-8)`) [`StoppingCriterion`](@ref)
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) リトラクションのタイプ
  * `vector_transport_method`: (`default_retraction_method(M, typeof(p))`) リトラクションのタイプ

# コンストラクタ

```
ConjugateGradientState(M, p)
```

最後の5つのフィールドはキーワードとして名前で設定でき、`X`はキーワード`initial_gradient`を使用して接ベクトル型に設定でき、デフォルトは`zero_vector(M,p)`であり、`δ`はこのベクトルのコピーに初期化されます。

# 参照

[`conjugate_gradient_descent`](@ref), [`DefaultManoptProblem`](@ref), [`ArmijoLinesearch`](@ref)
