```
splitdims(array, [dims])
```

`array`の内容をネストされた配列の配列に即座に分割します。最外の配列は指定された次元`dims`を含み、これは整数、整数のタプル、または最終的な配列の次元にデフォルトします。ネストされた配列は、残りのすべての次元を（昇順で）含みます。

同様の操作を遅延的に行う`splitdimsview`も参照してください。

#### 例:

```julia
julia> splitdims([1 2; 3 4])
2-element Array{Array{Int64,1},1}:
 [1, 3]
 [2, 4]

julia> splitdims([1 2; 3 4], 1)
2-element Array{Array{Int64,1},1}:
 [1, 2]
 [3, 4]
```
