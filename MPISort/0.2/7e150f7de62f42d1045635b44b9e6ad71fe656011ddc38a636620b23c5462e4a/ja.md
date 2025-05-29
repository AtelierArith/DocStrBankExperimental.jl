```julia
mutable struct SIHSortStats
```

ソート後に保存される有用な統計情報。

# メソッド

```
SIHSortStats(splitters, num_elements)
SIHSortStats(;splitters=nothing, num_elements=nothing)
```

# フィールド

  * `splitters::Union{Nothing, Vector}`: MPIランク間で要素を分割するために使用される値、長さ=`nranks - 1` デフォルト: nothing
  * `num_elements::Union{Nothing, Vector{Int64}}`: 各MPIランクにローカルに保存される要素の数、長さ=`nranks`。デフォルト: nothing
