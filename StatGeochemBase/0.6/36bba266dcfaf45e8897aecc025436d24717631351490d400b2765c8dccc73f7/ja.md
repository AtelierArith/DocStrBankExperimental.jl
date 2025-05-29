```julia
findnth(t::Collection{Bool}, n::Integer)
```

`t`の`n`番目の真の値のインデックスを返し、そうでなければ長さ(`t`)を返します。

### 例

```julia
julia> t = rand(Bool,5)
5-element Vector{Bool}:
 1
 1
 0
 1
 1

julia> findnth(t, 3)
4
```
