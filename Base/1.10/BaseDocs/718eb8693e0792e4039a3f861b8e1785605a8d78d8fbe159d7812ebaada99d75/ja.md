```
UndefVarError(var::Symbol)
```

現在のスコープにシンボルが定義されていません。

# 例

```jldoctest
julia> a
ERROR: UndefVarError: `a` not defined

julia> a = 1;

julia> a
1
```
