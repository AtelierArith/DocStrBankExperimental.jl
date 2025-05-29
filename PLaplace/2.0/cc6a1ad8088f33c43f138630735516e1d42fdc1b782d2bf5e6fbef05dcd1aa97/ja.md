```
assemble_derviativetensor_modified(
    D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}},
    nodesToDrop::Set{Int64};
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

ノードを削除することによって減少した新しい導関数テンソルを返します。例えば、メッシュの同次ディリクレ境界点を削除するために使用されます。
