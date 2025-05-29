```
Pointer(arr::AbstractArray)
```

引数配列のポインタを返します。また、ポインタのロードとストアのための補助関数も含まれています。

使用法

```julia-repl
julia> a = [1,2,3,4]
julia> pt = Pointer(a)
julia> pt[3]
3
```
