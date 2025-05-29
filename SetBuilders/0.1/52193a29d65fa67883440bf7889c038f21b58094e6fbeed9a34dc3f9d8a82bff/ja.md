```
SBSet - 型
```

`SBSet` 型は、すべての SetBuilders セット型のスーパタイプです。

# 例

```julia-repl
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> I isa SBSet
true
```
