```
BorderArray(inner::AbstractArray, border::AbstractBorder) <: AbstractArray
```

配列 `inner` の周りに指定された `border` を持つ薄いラッパーを構築します。コンストラクタではデータはコピーされず、代わりに `getindex` 呼び出しでボーダー値が動的に計算されます。ステンシル計算に便利です。詳細は [`padarray`](@ref) を参照してください。

# 例

```julia
julia> using ImageFiltering

julia> arr = reshape(1:6, (2,3))
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6

julia> BorderArray(arr, Pad((1,1)))
BorderArray{Int64,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}},Pad{2}} with indices 0:3×0:4:
 1  1  3  5  5
 1  1  3  5  5
 2  2  4  6  6
 2  2  4  6  6

julia> BorderArray(arr, Fill(10, (2,1)))
BorderArray{Int64,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}},Fill{Int64,2}} with indices -1:4×0:4:
 10  10  10  10  10
 10  10  10  10  10
 10   1   3   5  10
 10   2   4   6  10
 10  10  10  10  10
 10  10  10  10  10
```
