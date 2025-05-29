```
retrieve_symmetries(pge::PeriodicGraphEmbedding3D{T}, eqs::AbstractVector{S}=pge.cell.equivalents, vtypes=nothing, check_symmetry=check_valid_symmetry) where {T,S}
```

`(symgroup, discarded)`を返します。ここで、`symgroup`はグラフ埋め込み上の対称操作のリストを格納する[`SymmetryGroup3D`](@ref)です。これらの対称操作は、デフォルトでグラフ埋め込みの[`Cell`](@ref)に指定されたものから、[`EquivalentPosition`](@ref) `eqs`のリストから取得されます。`discarded`は、操作`eqs[i]`が周期グラフの実際の対称にマッピングできなかったために破棄されたインデックス`i`のリストです。

対称性を自動的に決定するには[`find_symmetries`](@ref)を参照し、`vtypes`および`check_symmetry`引数の定義については参照してください。
