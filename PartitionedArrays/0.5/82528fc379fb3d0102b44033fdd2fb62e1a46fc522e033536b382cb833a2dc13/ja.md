```
own_ghost_values(a::PSparseMatrix)
```

`a`の各部分における自身の行とゴースト列を含む行列のベクトルを取得します。

返される行列の*行*インデックスは、それぞれ[`own_to_global`](@ref)、[`own_to_local`](@ref)、および[`own_to_owner`](@ref)を使用して、グローバルインデックス、ローカルインデックス、およびオーナーにマッピングできます。

返される行列の*列*インデックスは、それぞれ[`ghost_to_global`](@ref)、[`ghost_to_local`](@ref)、および[`ghost_to_owner`](@ref)を使用して、グローバルインデックス、ローカルインデックス、およびオーナーにマッピングできます。
