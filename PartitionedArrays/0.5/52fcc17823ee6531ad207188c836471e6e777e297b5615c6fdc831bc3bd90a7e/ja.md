```
local_values(a::PSparseMatrix)
```

`a`の各部分に含まれるローカル行と列を含む行列のベクトルを取得します。

返される行列の行および列のインデックスは、それぞれ[`local_to_global`](@ref)、[`local_to_own`](@ref)、[`local_to_ghost`](@ref)、および[`local_to_owner`](@ref)を使用して、グローバルインデックス、所有インデックス、ゴーストインデックス、およびオーナーにマッピングできます。
