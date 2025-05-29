```
lead(v::AbstractArray, n = 1; default = missing)
```

配列 `v` を `n`（`Integer` または `Integer` のタプル）だけ負にシフトした `ShiftedArray` オブジェクトを遅延的に返します。`v` の次元数が `n` の長さを超える場合、残りの次元のシフトは `0` と見なされます。`default` は、元の配列の範囲外のときに返すデフォルト値を指定します。

# 例

```jldoctest lead
julia> v = [1, 3, 5, 4];

julia> ShiftedArrays.lead(v)
4-element ShiftedVector{Int64, Missing, Vector{Int64}}:
 3
 5
 4
  missing

julia> w = 1:2:9
1:2:9

julia> s = ShiftedArrays.lead(w, 2)
5-element ShiftedVector{Int64, Missing, StepRange{Int64, Int64}}:
 5
 7
 9
  missing
  missing

julia> copy(s)
5-element Vector{Union{Missing, Int64}}:
 5
 7
 9
  missing
  missing

julia> v = reshape(1:16, 4, 4);

julia> s = ShiftedArrays.lead(v, (0, 2))
4×4 ShiftedArray{Int64, Missing, 2, Base.ReshapedArray{Int64, 2, UnitRange{Int64}, Tuple{}}}:
  9  13  missing  missing
 10  14  missing  missing
 11  15  missing  missing
 12  16  missing  missing
```
