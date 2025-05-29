```
ghost_ghost_values(a::PSparseMatrix)
```

各部分の `a` に含まれるゴースト行と列を含む行列のベクトルを取得します。

返される行列の行および列のインデックスは、それぞれ [`ghost_to_global`](@ref)、[`ghost_to_local`](@ref)、および [`ghost_to_owner`](@ref) を使用して、グローバルインデックス、ローカルインデックス、およびオーナーにマッピングできます。
