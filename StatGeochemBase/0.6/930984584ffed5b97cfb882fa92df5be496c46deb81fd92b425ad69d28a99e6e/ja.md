```julia
delim_string_function(f, str, delim, T;
    	merge::Bool=false,
```

区切り文字 `delim` を使って区切られた文字列 `str` を解析し、関数 `f` によって操作される部分文字列に分割します。`f` の結果は、型 `T` の配列として返されます。

### 例

```julia
julia> delim_string_function(x -> delim_string_parse(x, ',', Int32, undefval=0), "1,2,3,4
5,6,7,8
9,10,11,12
13,14,15,16", '
', Array{Int32,1})
4-element Vector{Vector{Int32}}:
 [1, 2, 3, 4]
 [5, 6, 7, 8]
 [9, 10, 11, 12]
 [13, 14, 15, 16]
```
