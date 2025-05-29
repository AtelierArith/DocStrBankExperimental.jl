```
SetNeighbors <: SetNeighborhoodRule

SetNeighbors(f, neighborhood=Moor(1))
SetNeighbors{R,W}(f, neighborhood=Moor(1))
```

指定された近傍を持つ配列に手動で書き込むための [`SetCellRule`](@ref) です。近傍の外をインデックス指定することは未定義の動作です。

関数 `f` には4つの引数が渡されます：指定された [`SimData`](@ref) オブジェクト、指定された [`Neighborhood`](@ref) オブジェクト、セルのグリッド状態またはグリッド状態の `Tuple`、および現在のセルの `Tuple{Int,Int}` インデックスです。

グリッドを更新するには、[`add!`](@ref)、[`sub!`](@ref) を `Number` に、[`and!`](@ref)、[`or!`](@ref) を `Bool` に使用できます。これらのメソッドは、すべてのグリッドセルからの安全に結合された書き込みを行うことができます。

`setindex!` を直接使用することも可能ですが、複数のセルが予測不可能な順序で同じ場所に書き込む可能性があるため、バグを引き起こす可能性があります。一般的に、近傍インデックスを直接設定するのは、常に同じ値を設定する場合のみ行うべきです。そうすれば、他のグリッドセルからの書き込みが同じ結果に達することが保証されます。

[`neighbors`](@ref)、[`offsets`](@ref) および [`positions`](@ref) は `SetNeighbors` ルールにとって便利なメソッドです。

## 例

この例では、すべての隣接セルに値を追加します：

```jldoctest
using DynamicGrids

rule = SetNeighbors{:a}() do data, neighborhood, a, I
    add_to_neighbors = your_func(a)
    for pos in positions(neighborhood)
        add!(data[:b], add_to_neighbors, pos...)
    end
end
# output
SetNeighbors{:a,:a}(
    f = var"#1#2"
    neighborhood = Moore{1, 2, 8, Nothing}
)
```
