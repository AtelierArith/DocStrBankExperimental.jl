```
has_duals(model::Model; result::Int = 1)
```

結果インデックス `result` でクエリ可能な双対解がソルバーに存在する場合は `true` を返し、そうでない場合は `false` を返します。

[`dual`](@ref)、[`shadow_price`](@ref)、および [`result_count`](@ref) も参照してください。
