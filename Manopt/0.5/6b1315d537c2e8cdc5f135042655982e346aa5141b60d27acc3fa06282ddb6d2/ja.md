```
WolfePowellBinaryLinesearch(; kwargs...)
WolfePowellBinaryLinesearch(M::AbstractManifold; kwargs...)
```

与えられた十分な減少係数 $c_1$ と十分な曲率条件係数 $c_2$ に対して、Armijo-Goldstein 条件を満たすためにラインサーチを実行します。より単純な方法を試みる [`WolfePowellLinesearch`](@ref Manopt.WolfePowellLinesearch) と比較して、このラインサーチは以下のアルゴリズムを実行します。

ここで

$$
A(t) = f(p_+) ≤ c_1 t ⟨\operatorname{grad}f(p), X⟩_{x}
\quad\text{ および }\quad
W(t) = ⟨\operatorname{grad}f(x_+), \mathcal T_{p_+←p}X⟩_{p_+} ≥ c_2 ⟨X, \operatorname{grad}f(x)⟩_x,
$$

$$
p_+ =\operatorname{retr}_p(tX)
$$

は現在の試行点であり、$\mathcal T_{⋅←⋅}$ はベクトル輸送を示します。次に、[Huang:2014](@cite) のアルゴリズム 7 に類似した以下のアルゴリズムが実行されます。

1. $$
    α=0
    $$

    , $β=∞$ および $t=1$ を設定します。
2. $$
    A(t)
    $$

    または $W(t)$ のいずれかが成り立たない限り、ステップ 3-5 を実行します。
3. $$
    A(t)
    $$

    が失敗した場合、$β=t$ を設定します。
4. $$
    A(t)
    $$

    が成り立つが $W(t)$ が失敗した場合、$α=t$ を設定します。
5. $$
    β<∞
    $$

    の場合は $t=\frac{α+β}{2}$ を設定し、そうでない場合は $t=2α$ を設定します。

# キーワード引数

  * `sufficient_decrease=10^(-4)`
  * `sufficient_curvature=0.999`
  * `max_stepsize=`[`max_stepsize`](@ref)`(M, p)`: ここで許可される最大ステップサイズ。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、再収束に関する[セクション](@extref ManifoldsBase :doc:`retractions`)を参照してください。
  * `stop_when_stepsize_less=0.0`: 停止する最小ステップサイズ（最後のものが取られます）
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関する[セクション](@extref ManifoldsBase :doc:`vector_transports`)を参照してください。

```
