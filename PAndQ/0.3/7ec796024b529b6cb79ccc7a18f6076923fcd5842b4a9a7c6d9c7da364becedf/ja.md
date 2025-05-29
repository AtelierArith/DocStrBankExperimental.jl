```
atoms(p)
```

`p`に含まれる各原子命題のイテレータを返します。

# 例

```jldoctest
julia> @atomize collect(atoms(p ∧ q))
2-element Vector{PAndQ.Variable}:
 p
 q
```
