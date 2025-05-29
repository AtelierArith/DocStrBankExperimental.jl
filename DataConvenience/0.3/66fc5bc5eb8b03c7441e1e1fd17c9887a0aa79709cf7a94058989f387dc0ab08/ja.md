```
StringVector(v::CategoricalVector{String})
```

`v::CategoricalVector`を効率的にWeakRefStrings.StringVectorに変換します。

## 例

```julia
using DataFrames
a  = categorical(["a","c", "a"])
a.refs
a.pool.index

# 効率的に変換
sa = StringVector(a)

sa.buffer
sa.lengths
sa.offsets
```
