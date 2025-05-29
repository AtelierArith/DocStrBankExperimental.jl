```
own_own_values(a::PSparseMatrix)
```

行列 `a` の各部分に含まれる自身の行と列を含む行列のベクトルを取得します。

返される行列の行および列のインデックスは、それぞれ [`own_to_global`](@ref)、[`own_to_local`](@ref)、および [`own_to_owner`](@ref) を使用して、グローバルインデックス、ローカルインデックス、およびオーナーにマッピングできます。
