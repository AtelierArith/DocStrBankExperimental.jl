```
local_values(a::PVector)
```

`a`の各部分に含まれるローカル値のベクトルのベクトルを取得します。

返されるベクトルのインデックスは、それぞれ[`local_to_global`](@ref)、[`local_to_own`](@ref)、[`local_to_ghost`](@ref)、および[`local_to_owner`](@ref)を使用して、グローバルインデックス、所有インデックス、ゴーストインデックス、およびオーナーにマッピングできます。
