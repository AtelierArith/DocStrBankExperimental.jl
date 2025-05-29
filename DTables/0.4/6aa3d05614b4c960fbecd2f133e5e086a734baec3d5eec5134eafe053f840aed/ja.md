```
groupby(d::DTable, col::Symbol; merge=true, chunksize=0) -> GDTable
```

`d`を列`col`の異なる値でグループ化します。

グループ化のプロセスは、`merge`および`chunksize`というキーワード引数を提供することで影響を受ける可能性があります。デフォルトでは、単一のキーに属するすべてのチャンクは、単一のパーティションにマージされます。`chunksize`に正の値を指定すると、より小さなパーティションを`chunksize`を超えないパーティションにマージしようとします。`chunksize`を超えるパーティションは、`chunksize`のパーティションに分割されることはないことに注意してください。`merge=false`を指定することで、マージを完全に無効にすることができます。

# 例

```julia
julia> d = DTable((a=shuffle(repeat('a':'d', inner=4, outer=4)),), 4)
DTable with 16 partitions
Tabletype: NamedTuple

julia> DTables.groupby(d, :a)
GDTable with 4 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]

julia> DTables.groupby(d, :a, chunksize=3)
GDTable with 24 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]

julia> DTables.groupby(d, :a, merge=false)
GDTable with 42 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]
```
