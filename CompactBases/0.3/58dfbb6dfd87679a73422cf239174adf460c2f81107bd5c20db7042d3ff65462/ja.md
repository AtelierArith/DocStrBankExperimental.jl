```
numfunctions(t)
```

ノットセット`t`によって生成される基底関数の数を返します。

# 例

```jldoctest
julia> numfunctions(LinearKnotSet(3, 0, 1, 2))
4

julia> numfunctions(LinearKnotSet(5, 0, 1, 2))
6
```
