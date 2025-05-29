```
print_dimacs(io = stdout, p)
```

`p`のDIMACS形式を出力します。

`io`は、書き込むための`IO`またはファイルパス`String`です。

# 例

```jldoctest
julia> @atomize print_dimacs(p ∧ q)
p cnf 2 2
1 0
2 0

julia> @atomize print_dimacs(p ↔ q)
p cnf 2 2
1 -2 0
-1 2 0
```
