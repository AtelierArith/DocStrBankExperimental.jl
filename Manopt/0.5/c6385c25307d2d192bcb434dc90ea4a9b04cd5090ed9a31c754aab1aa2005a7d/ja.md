```
PolakRibiereCoefficient(; kwargs...)
PolakRibiereCoefficient(M::AbstractManifold; kwargs...)
```

[`conjugate_gradient_descent`](@ref)アルゴリズムのための更新係数を、Riemann多様体に適応された[PolakRibiere:1969](@cite)に基づいて計算します。

最後の反復と勾配を$p_k,X_k$、現在の反復と勾配を$p_{k+1}, X_{k+1}$、最後の更新方向を$δ_k$とします。

$$
ν_k = X_{k+1} - \mathcal T_{p_{k+1}←p_k}X_k
$$

と定義します。ここで、$\mathcal T_{⋅←⋅}$はベクトル輸送を示します。

係数は次のように表されます。

$$
β_k = \frac{⟨ X_{k+1}, ν_k ⟩_{p_{k+1}}}{\lVert X_k \rVert_{{p_k}}^2}.
$$

# キーワード引数

  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、詳細は[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照してください。

!!! info
    この関数は[`PolakRibiereCoefficientRule`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。


```
