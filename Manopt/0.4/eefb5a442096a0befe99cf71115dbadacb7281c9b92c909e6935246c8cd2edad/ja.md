```
conjugate_gradient_descent(M, F, gradF, p=rand(M))
conjugate_gradient_descent(M, gradient_objective, p)

共役勾配に基づく降下を実行します。

```

math p*{k+1} = \operatorname{retr}*{p*k} \bigl( s*kδ_k \bigr),

```

ここで、$\operatorname{retr}$は`Manifold` `M`上のリトラクションを示し、降下方向$δ_k$を更新するために、前の方向$δ_{k-1}$と両方の勾配$\operatorname{grad}f(x_k)$、$\operatorname{grad}f(x_{k-1})$に基づいて異なるルールを使用できます。[`Stepsize`](@ref) $s_k$は[`Linesearch`](@ref)によって決定される場合があります。

`f`と`grad_f`の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective`を直接提供できます。

利用可能な更新ルールは、[`SteepestDirectionUpdateRule`](@ref)で、これは[`gradient_descent`](@ref)を生成し、[`ConjugateDescentCoefficient`](@ref)（デフォルト）、[`DaiYuanCoefficient`](@ref)、[`FletcherReevesCoefficient`](@ref)、[`HagerZhangCoefficient`](@ref)、[`HestenesStiefelCoefficient`](@ref)、[`LiuStoreyCoefficient`](@ref)、および[`PolakRibiereCoefficient`](@ref)です。これらはすべて[`ConjugateGradientBealeRestart`](@ref)ルールと組み合わせることができます。

これらはすべて$β_k$を計算し、このアルゴリズムは探索方向を次のように更新します。

```

math \delta*k=\operatorname{grad}f(p*k) + β*k \delta*{k-1}

```

# 入力

  * `M`      多様体 $\mathcal M$
  * `f`      最小化するコスト関数 $F:\mathcal M→ℝ$、関数として実装 `(M,p) -> v`
  * `grad_f` コスト関数 $F$ の勾配 $\operatorname{grad}F:\mathcal M → T\mathcal M$、同様に `(M,x) -> X` として実装
  * `p`      初期値 $x∈\mathcal M$

# オプション

  * `coefficient`:             ([`ConjugateDescentCoefficient`](@ref) `<:` [`DirectionUpdateRule`](@ref)) 降下方向更新係数 $β_k$ を計算するルール、ファンクタとして、結果の関数マップは `(amp, cgs, i) -> β` で、`amp` は[`AbstractManoptProblem`](@ref)、`cgs` は[`ConjugateGradientDescentState`](@ref)、`i` は現在の反復です。
  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するかどうかを指定（デフォルト）`gradF(M, x)`の形式または[`InplaceEvaluation`](@ref)の形式`gradF!(M, X, x)`。
  * `retraction_method`: (`default_retraction_method(M, typeof(p))`) 使用するリトラクションメソッド。
  * `stepsize`:                ([`ArmijoLinesearch`](@ref)経由[`default_stepsize`](@ref)) 探索方向に適用される[`Stepsize`](@ref)関数。デフォルトは定数ステップサイズ1です。
  * `stopping_criterion`:      (`stopWhenAny( stopAtIteration(200), stopGradientNormLess(10.0^-8))`) 停止するタイミングを示す関数。
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) 新しい降下方向を計算する際に古い降下方向を輸送するためのベクトル輸送メソッド。

[`ManifoldGradientObjective`](@ref)を直接提供する場合、`evaluation`は無視されます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細は[`get_solver_return`](@ref)を参照してください。
```
