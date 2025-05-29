```
lead(v::AbstractArray, n = 1; default = missing)
```

`v`を基にした`ShiftedArray`オブジェクトを返します。第二引数は各次元での負のシフト量を指定します。整数の場合、最初の次元を指すと見なされます。`default`は、範囲外のときのデフォルト値を指定します。

# 例

```jldoctest lead
julia> v = [1, 3, 5, 4];

julia> lead(v)
4-element ShiftedArray{Int64,Missing,1,Array{Int64,1}}:
 3
 5
 4
  missing

julia> w = 1:2:9
1:2:9

julia> s = lead(w, 2)
5-element ShiftedArray{Int64,Missing,1,StepRange{Int64,Int64}}:
 5
 7
 9
  missing
  missing

julia> copy(s)
5-element Array{Union{Missing, Int64},1}:
 5
 7
 9
  missing
  missing

julia> v = reshape(1:16, 4, 4);

julia> s = lead(v, (0, 2))
4×4 ShiftedArray{Int64,Missing,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}}}:
  9  13  missing  missing
 10  14  missing  missing
 11  15  missing  missing
 12  16  missing  missing
```
