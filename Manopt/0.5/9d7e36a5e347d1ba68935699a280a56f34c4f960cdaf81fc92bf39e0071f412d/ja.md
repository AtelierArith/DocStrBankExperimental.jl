```
WolfePowellLinesearch(; kwargs...)
WolfePowellLinesearch(M::AbstractManifold; kwargs...)
```

両方のArmijo-Goldstein条件を満たすためにラインサーチを実行します。

$$
f\bigl( \operatorname{retr}_{p}(αX) \bigr) ≤ f(p) + c_1 α_k ⟨\operatorname{grad} f(p), X⟩_{p}
$$

およびWolfe条件

$$
\frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_{p}(tX)\bigr)
\Big\vert_{t=α}
≥ c_2 \frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_{p}(tX)\bigr)\Big\vert_{t=0}.
$$

与えられた十分な減少係数$c_1$と十分な曲率条件係数$c_2$に対して。

これは[NocedalWright:2006; Section 3.1](@cite)から採用されています。

# キーワード引数

  * `sufficient_decrease=10^(-4)`
  * `sufficient_curvature=0.999`
  * `p::P`: 候補の一時的なストレージとしての多様体$\mathcal M$上の点
  * `X::T`: 多様体$\mathcal M$上の点$p$での接ベクトル、候補の方向と接線のために割り当てられたメモリの型
  * `max_stepsize=`[`max_stepsize`](@ref)`(M, p)`: ここで許可される最大ステップサイズ。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束$\operatorname{retr}$、[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stop_when_stepsize_less=0.0`: 停止する際の最小ステップサイズ（最後のものが取られる）
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

```
