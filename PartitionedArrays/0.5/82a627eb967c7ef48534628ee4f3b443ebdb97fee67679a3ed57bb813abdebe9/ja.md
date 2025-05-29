```
ghost_values(a::PVector)
```

`a`の各部分に含まれるゴースト値を含むベクトルのベクトルを取得します。

返される行列のインデックスは、それぞれ[`ghost_to_global`](@ref)、[`ghost_to_local`](@ref)、および[`ghost_to_owner`](@ref)を使用して、グローバルインデックス、ローカルインデックス、およびオーナーにマッピングできます。
