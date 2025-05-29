```
ConjugateGradientBealeRestart(direction_update::Union{DirectionUpdateRule,ManifoldDefaultsFactory}; kwargs...)
ConjugateGradientBealeRestart(M::AbstractManifold, direction_update::Union{DirectionUpdateRule,ManifoldDefaultsFactory}; kwargs...)
```

2つの方向がほぼ直交しているときに、再起動の可能性を持つ共役勾配係数を計算します。詳細は[HagerZhang:2006; page 12](@cite)（プレプリントでは、ジャーナルのページ番号で46ページ）を参照してください。この手法は、1972年のE. Bealeの会議論文にちなんで名付けられました[Beale:1972](@cite)。この手法は、既存の[`DirectionUpdateRule`](@ref) `direction_update`に対する*デコレーター*として機能します。

最後の反復と勾配を$p_k,X_k$、現在の反復と勾配を$p_{k+1}, X_{k+1}$、最後の更新方向を$δ_k$とします。

再起動が行われる場合、次の条件が満たされると$β_k = 0$が返されます。

$$
  \frac{⟨X_{k+1}, \mathcal T_{p_{k+1}←p_k}X_k⟩}{\lVert X_k \rVert_{p_k}} > ε,
$$

ここで、$ε$は`threshold`であり、デフォルトでは`0.2`に設定されています。詳細は[Powell:1977](@cite)を参照してください。

## 入力

  * `direction_update`: [`DirectionUpdateRule`](@ref)またはそのようなルールを生成する対応する[`ManifoldDefaultsFactory`](@ref)。

## キーワード引数

  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、詳細は[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照してください。
  * `threshold=0.2`

!!! info
    この関数は[`ConjugateGradientBealeRestartRule`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。 manifoldに依存するデフォルト値については、このファクトリーは、例えば対応する[`AbstractManoptSolverState`](@ref)から利用可能なmanifoldが得られるまで構築を延期します。


```
