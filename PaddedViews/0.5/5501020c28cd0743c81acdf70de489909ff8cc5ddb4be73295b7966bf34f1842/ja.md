```
datapadded = PaddedView(fillvalue, data, padded_axes)
datapadded = PaddedView(fillvalue, data, padded_axes, data_axes)
datapadded = PaddedView(fillvalue, data, sz)
datapadded = PaddedView(fillvalue, data, sz, first_datum)
datapadded = PaddedView{T}(args...)
```

配列 `data` のパディングされたバージョンを作成します。`data` に割り当てられていない `padded_axes` の範囲内の要素は、`fillvalue` の値を持ちます。

`data_axes` を指定して `data` の代替の軸セットを指定することで、`data` を異なるインデックスのセットに移動させることができます。これは次のように短縮できます。

```
offsetdata = OffsetArray(data, data_axes)
datapadded = PaddedView(fillvalue, offsetdata, padded_axes)
```

これは [OffsetArrays](https://github.com/JuliaArrays/OffsetArrays.jl) パッケージを使用しています。

また、パディングされた配列のサイズ `sz` を指定することもでき、その場合 `datapadded` は 1 からインデックスを開始します。オプションで、`first_datum` を使用して `data` の `[1, 1, ...]` 要素の位置を指定できます。具体的には、`datapadded[first_datum...]` は `data[1, 1, ...]` に対応します。`first_datum` のデフォルトはすべて 1 です。

ビューのエルタイプ `T` はオプションです。指定されていない場合、ほとんどの場合、`T` は `eltype(data)` と推測されます。`fillvalue` が `eltype(data)` に変換できない場合、`T` は変換できるものに昇格されます。たとえば、`fillvalue == nothing` で `eltype(data) == Float32` の場合、推測されるエルタイプ `T` は `Union{Nothing, Float32}` になります。

# 例

```jldoctest
julia> using PaddedViews

julia> a = collect(reshape(1:9, 3, 3))
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> PaddedView(-1, a, (4, 5))
4×5 PaddedView(-1, ::Matrix{Int64}, (Base.OneTo(4), Base.OneTo(5))) with eltype Int64:
  1   4   7  -1  -1
  2   5   8  -1  -1
  3   6   9  -1  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (1:5,1:5), (2:4,2:4))
5×5 PaddedView(-1, OffsetArray(::Matrix{Int64}, 2:4, 2:4), (1:5, 1:5)) with eltype Int64 with indices 1:5×1:5:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (0:4, 0:4))
5×5 PaddedView(-1, ::Matrix{Int64}, (0:4, 0:4)) with eltype Int64 with indices 0:4×0:4:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1

julia> PaddedView(-1, a, (5,5), (2,2))
5×5 PaddedView(-1, OffsetArray(::Matrix{Int64}, 2:4, 2:4), (Base.OneTo(5), Base.OneTo(5))) with eltype Int64:
 -1  -1  -1  -1  -1
 -1   1   4   7  -1
 -1   2   5   8  -1
 -1   3   6   9  -1
 -1  -1  -1  -1  -1
```
