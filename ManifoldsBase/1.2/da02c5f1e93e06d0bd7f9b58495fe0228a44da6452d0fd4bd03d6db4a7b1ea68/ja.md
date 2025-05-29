```
default_approximation_method(M::AbstractManifold, f)
default_approximation_method(M::AbtractManifold, f, T)
```

[`AbstractManifold`](@ref) に対してデフォルトの推定方法を指定し、特定の関数 `f` と、オプションで `M` 上の異なる（点またはベクトル）表現を区別するための型 `T` を指定します。

デフォルトでは、すべての関数 `f` は単に多様体のためのシグネチャを呼び出します。例外的な関数は次のとおりです：

  * `retract` および `retract!` は [`default_retraction_method`](@ref) にフォールバックします
  * `inverse_retract` および `inverse_retract!` は [`default_inverse_retraction_method`](@ref) にフォールバックします
  * ベクトル輸送メソッドのいずれかは [`default_vector_transport_method`](@ref) にフォールバックします
