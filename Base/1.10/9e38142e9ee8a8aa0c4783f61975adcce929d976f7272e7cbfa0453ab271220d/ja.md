```
nand(x, y)
⊼(x, y)
```

`x` と `y` のビット単位の nand (not and)。[三値論理](https://en.wikipedia.org/wiki/Three-valued_logic)を実装しており、引数の一つが `missing` の場合は [`missing`](@ref) を返します。

中置演算 `a ⊼ b` は `nand(a,b)` の同義語であり、`⊼` は Julia REPL で `\nand` または `\barwedge` をタブ補完することで入力できます。

# 例

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
