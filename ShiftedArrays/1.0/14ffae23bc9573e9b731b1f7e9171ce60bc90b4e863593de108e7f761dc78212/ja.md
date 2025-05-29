```
lag(v::AbstractArray, n = 1; default = missing)
```

`v`を基にした`ShiftedArray`オブジェクトを返します。2番目の引数は各次元でのシフト量を指定します。整数の場合、最初の次元を指すと見なされます。`default`は、範囲外のときのデフォルト値を指定します。

# 例

```jldoctest lag
julia> v = [1, 3, 5, 4];

julia> lag(v)
4-element ShiftedArray{Int64,Missing,1,Array{Int64,1}}:
  missing
 1
 3
 5

julia> w = 1:2:9
1:2:9

julia> s = lag(w, 2)
5-element ShiftedArray{Int64,Missing,1,StepRange{Int64,Int64}}:
  missing
  missing
 1
 3
 5

julia> copy(s)
5-element Array{Union{Missing, Int64},1}:
  missing
  missing
 1
 3
 5

julia> v = reshape(1:16, 4, 4);

julia> s = lag(v, (0, 2))
4×4 ShiftedArray{Int64,Missing,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}}}:
 missing  missing  1  5
 missing  missing  2  6
 missing  missing  3  7
 missing  missing  4  8
```
