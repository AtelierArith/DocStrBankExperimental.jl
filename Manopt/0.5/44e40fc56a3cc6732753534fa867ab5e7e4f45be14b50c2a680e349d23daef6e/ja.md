```
Nesterov(; kwargs...)
Nesterov(M::AbstractManifold; kwargs...)
```

$$
f
$$

が$L$-リプシッツかつ$μ$-強凸であると仮定します。次の条件が与えられたときに、

  * ステップサイズ$h_k<\frac{1}{L}$（[`GradientDescentState`](@ref)から）
  * `shrinkage`パラメータ$β_k$
  * 現在の反復$p_k$
  * 前の反復からの中間値$γ_k$と$v_k$

次のステップを使用してNesterovタイプの更新を計算します。詳細は[ZhangSra:2018](@cite)を参照してください。

1. $$
    α^2 = h_k\bigl((1-α_k)γ_k+α_k μ\bigr)
    $$

    の正の根$α_k∈(0,1)$を計算します。
2. $$
    \barγ_k+1 = (1-α_k)γ_k + α_kμ
    $$

    を設定します。
3. $$
    y_k = \operatorname{retr}_{p_k}\Bigl(\frac{α_kγ_k}{γ_k + α_kμ}\operatorname{retr}^{-1}_{p_k}v_k \Bigr)
    $$
4. $$
    x_{k+1} = \operatorname{retr}_{y_k}(-h_k \operatorname{grad}f(y_k))
    $$
5. $$
    v_{k+1} = \operatorname{retr}_{y_k}\Bigl(\frac{(1-α_k)γ_k}{\barγ_k}\operatorname{retr}_{y_k}^{-1}(v_k) - \frac{α_k}{\barγ_{k+1}}\operatorname{grad}f(y_k) \Bigr)
    $$
6. $$
    γ_{k+1} = \frac{1}{1+β_k}\barγ_{k+1}
    $$

次に、$p_k$から$p_k+1$への方向$d = \operatorname{retr}^{-1}_{p_k}p_{k+1}$が返されます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体$\mathcal M$（オプション）

# キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体$\mathcal M$上の点
  * `γ=0.001`
  * `μ=0.9`
  * `shrinkage = k -> 0.8`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆リトラクション$\operatorname{retr}^{-1}$、詳細は[リトラクションとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください。

!!! info
    この関数は[`NesterovRule`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。


```
