```
DaiYuanCoefficient(; kwargs...)
DaiYuanCoefficient(M::AbstractManifold; kwargs...)
```

[`conjugate_gradient_descent`](@ref)アルゴリズムのための更新係数を、Riemannian多様体に適応された[DaiYuan:1999](@cite)に基づいて計算します。

最後の反復と勾配を$p_k,X_k$、現在の反復と勾配を$p_{k+1}, X_{k+1}$、最後の更新方向を$δ_k$とします。

$$
ν_k = X_{k+1} - \mathcal T_{p_{k+1}←p_k}X_k
$$

と定義します。ここで、$\mathcal T_{⋅←⋅}$はベクトル輸送を示します。

係数は次のように表されます。

$$
β_k =
\frac{\lVert X_{k+1} \rVert_{p_{k+1}}^2}{⟨\mathcal T_{p_{k+1}←p_k}δ_k, ν_k⟩_{p_{k+1}}}
$$

# キーワード引数

  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照してください。

!!! info
    この関数は[`DaiYuanCoefficientRule`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値については、このファクトリは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。

