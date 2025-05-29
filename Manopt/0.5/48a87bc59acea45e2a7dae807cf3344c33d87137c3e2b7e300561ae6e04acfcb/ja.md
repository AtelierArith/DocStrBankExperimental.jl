```
NelderMead(M::AbstractManifold, f, population=NelderMeadSimplex(M))
NelderMead(M::AbstractManifold, mco::AbstractManifoldCostObjective, population=NelderMeadSimplex(M))
NelderMead!(M::AbstractManifold, f, population)
NelderMead!(M::AbstractManifold, mco::AbstractManifoldCostObjective, population)
```

コスト関数 $f: \mathcal M → ℝ$ に対するネルダー・ミード最小化問題を、マニフォールド `M` 上で解きます。初期の [`NelderMeadSimplex`](@ref) が提供されていない場合、ランダムな点の集合が選択されます。計算は `population` のインプレースで実行できます。

アルゴリズムは以下のステップで構成されています。$d$ をマニフォールド $\mathcal M$ の次元とします。

1. シンプルックスの頂点 $p_i, i=1,…,d+1$ をコストが増加するように順序付け、$f(p_1) ≤ f(p_2) ≤ … ≤ f(p_{d+1})$ となるようにします。
2. シンプルックスの頂点 $p_1,…,p_{d+1}$ のリーマン中心 [Karcher:1977](@cite) を計算し、$p_{\text{m}}$ を求めます。cf. [`mean`](@extref Statistics.mean-Tuple{AbstractManifold, Vararg{Any}})。
3. 最悪の点を平均で反射させます。$p_{\text{r}} = \operatorname{retr}_{p_{\text{m}}}\bigl( - α\operatorname{retr}^{-1}_{p_{\text{m}}} (p_{d+1}) \bigr)$ もし $f(p_1) ≤ f(p_{\text{r}}) ≤ f(p_{d})$ ならば、$p_{d+1} = p_{\text{r}}$ と設定し、ステップ1に戻ります。
4. もし $f(p_{\text{r}}) < f(p_1)$ ならばシンプルックスを拡張します。拡張点 $p_{\text{e}} = \operatorname{retr}_{p_{\text{m}}}\bigl( - γα\operatorname{retr}^{-1}_{p_{\text{m}}} (p_{d+1}) \bigr)$ を計算します。この定式化では、以前の逆引きからの接ベクトルを再利用できます。もし $f(p_{\text{e}}) < f(p_{\text{r}})$ ならば $p_{d+1} = p_{\text{e}}$ とし、そうでなければ $p_{d+1} = p_{\text{r}}$ とします。次にステップ1に戻ります。
5. もし $f(p_{\text{r}}) ≥ f(p_d)$ ならばシンプルックスを収縮します。

    1. もし $f(p_{\text{r}}) < f(p_{d+1})$ ならば、ステップ $s = -ρ$ とします。
    2. そうでなければ、$s=ρ$ とします。

    収縮点 $p_{\text{c}} = \operatorname{retr}_{p_{\text{m}}}\bigl(s\operatorname{retr}^{-1}_{p_{\text{m}}} p_{d+1} \bigr)$ を計算します。

    1. この場合、もし $f(p_{\text{c}}) < f(p_{\text{r}})$ ならば $p_{d+1} = p_{\text{c}}$ とし、ステップ1に戻ります。
    2. この場合、もし $f(p_{\text{c}}) < f(p_{d+1})$ ならば $p_{d+1} = p_{\text{c}}$ とし、ステップ1に戻ります。
6. すべての点を縮小します（$p_1$ に近づけます）。すべての $i=2,...,d+1$ に対して、$p_{i} = \operatorname{retr}_{p_{1}}\bigl( σ\operatorname{retr}^{-1}_{p_{1}} p_{i} \bigr)$ と設定します。

詳細については、ウィキペディアのユークリッド版 [https://en.wikipedia.org/wiki/Nelder-Mead_method](https://en.wikipedia.org/wiki/Nelder-Mead_method) または [http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf](http://www.optimization-online.org/DB_FILE/2007/08/1742.pdf) のアルゴリズム 4.1 を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `population::`[`NelderMeadSimplex`](@ref)`=`[`NelderMeadSimplex`](@ref)`(M)`: $d+1$ 点の初期シンプルックス、ここで $d$ は `M` の [`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`) です。

# キーワード引数

  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`[`|`](@ref StopWhenAny)[`StopWhenPopulationConcentrated`](@ref)`()`: 停止基準が満たされたことを示すファンクタ [`StoppingCriterion`](@ref)
  * `α=1.0`: 反射パラメータ $α > 0$:
  * `γ=2.0` 拡張パラメータ $γ$:
  * `ρ=1/2`: 収縮パラメータ、$0 < ρ ≤ \frac{1}{2}$,
  * `σ=1/2`: 縮小係数、$0 < σ ≤ 1$
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、特に `return_state=` キーワードについては [`get_solver_return`](@ref) を参照してください。
