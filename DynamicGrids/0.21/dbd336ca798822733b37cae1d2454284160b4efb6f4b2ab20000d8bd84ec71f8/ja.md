```
SetCell <: SetCellRule

SetCell(f)
SetCell{R,W}(f)
```

手動で必要な場所に配列に書き込むための [`SetCellRule`](@ref) です。`f` には [`AbstractSimData`](@ref) オブジェクト、セルのグリッド状態またはグリッド状態の `Tuple` と現在のセルの `Tuple{Int,Int}` インデックスが渡されます。

グリッドを更新するには、[`add!`](@ref)、`Number` 用の [`sub!`](@ref)、および `Bool` 用の [`and!`](@ref)、[`or!`](@ref) を使用できます。これらのメソッドは、すべてのグリッドセルからの安全な書き込みを組み合わせます - `setindex!` を直接使用するとバグが発生します。

## 例

宛先セルを選択し、それがグリッド内にある場合は、両方のグリッドの状態に基づいて更新します：

```jldoctest SetCell
using DynamicGrids
rule = SetCell{Tuple{:a,:b},:b}() do data, (a, b), I 
    dest = your_dest_pos_func(I)
    if isinbounds(data, dest)
        destval = your_dest_val_func(a, b)
        add!(data[:b], destval, dest...)
    end
end

# output
SetCell{Tuple{:a, :b},:b}(
    f = var"#1#2"
)
```
