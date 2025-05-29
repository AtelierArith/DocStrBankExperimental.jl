```
mapmany(f, a...)
```

`map`のように、しかし`f(x)`が各`x ∈ a`に対して出力に挿入する任意の数の値を返すことができます。

# 例

```jldoctest
julia> mapmany(x -> 1:x, [1,2,3])
6-element Array{Int64,1}:
 1
 1
 2
 1
 2
 3
```
