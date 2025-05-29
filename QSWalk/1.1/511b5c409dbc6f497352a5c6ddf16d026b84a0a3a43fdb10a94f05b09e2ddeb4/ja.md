```
default_nm_loc_ham(size)
```

サイズ `size`×`size` のデモラリゼーション手法のためのデフォルトローカルハミルトニアンを返します。ハミルトニアンはスパースで、最初の上対角線（`1im` に等しい）と下対角線（`-1im` に等しい）に非ゼロ要素があります。

*注意:* この関数は `nm_loc_ham` 関数のデフォルト引数を提供するために使用されます。

# 例

```jldoctest; setup = :(using QSWalk)
julia> QSWalk.default_nm_loc_ham(4)
4×4 SparseArrays.SparseMatrixCSC{Complex{Float64},Int64} with 6 stored entries:
  [2, 1]  =  0.0-1.0im
  [1, 2]  =  0.0+1.0im
  [3, 2]  =  0.0-1.0im
  [2, 3]  =  0.0+1.0im
  [4, 3]  =  0.0-1.0im
  [3, 4]  =  0.0+1.0im
```
