```
DefaultMeshAdaptiveDirectSearch <: AbstractMeshSearchFunction
```

# ファンクタ

```
(s::DefaultMeshAdaptiveDirectSearch)(problem, mesh_size::Real, X; scale_mesh::Real=1.0, max_stepsize::Real=inf)
```

# フィールド

  * `q`: 多様体上の点のための一時的なメモリ
  * `X`: 探索を行うための情報、例えば、ポールによって見つかった最後の方向。
  * `last_search_improved::Bool` 最後の探索が成功したかどうか、すなわちコストが改善されたかを示す。
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、詳細は[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照。

# コンストラクタ

```
DefaultMeshAdaptiveDirectSearch(M::AbstractManifold, p=rand(M); kwargs...)
```

## キーワード引数

  * `X::T=zero_vector(M, p)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、詳細は[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照。
