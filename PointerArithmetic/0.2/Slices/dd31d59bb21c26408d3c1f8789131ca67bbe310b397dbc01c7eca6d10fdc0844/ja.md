```
shift_end(sl::Slice, i::Integer)
```

配列の終了点を特定の数のアイテム分シフトします。`>>`を使用して呼び出すことができます。使用法:

```julia-repl
julia> arr = [1,2,3,4]
julia> sl = Slice(arr, 2:3)
2-element Slice{Int64}:
2
3
julia> sl >> 1
3-element Slice{Int64}:
2
3
4
julia> sl >> -1
1-element Slice{Int64}:
2
```
