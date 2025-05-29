```
sign(g::Perm)
```

置換の符号を返します。

`sign`は、`g`が偶数の場合は$1$を、奇数の場合は$-1$を返します。`sign`は、交代群の核を持つ置換群から$\mathbb{Z}$の単位群への準同型を表します。

# 例

```jldoctest
julia> g = Perm([3,4,1,2,5])
(1,3)(2,4)

julia> sign(g)
1

julia> g = Perm([3,4,5,2,1,6])
(1,3,5)(2,4)

julia> sign(g)
-1
```
