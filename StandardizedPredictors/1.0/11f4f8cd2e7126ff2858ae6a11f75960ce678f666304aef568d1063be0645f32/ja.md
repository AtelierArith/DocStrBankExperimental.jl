```
struct Center
```

中心化スキームを表し、`StatsModels.AbstractContrasts`に似ています。`schema`へのヒントとして`Dict`に値として渡すか、`fit`の`contrasts`キーワード引数として渡します。

## 例

使用する中心値を指定できます：

```
julia> schema((x=collect(1:10), ), Dict(:x => Center(5)))
StatsModels.Schema with 1 entry:
  x => center(x, 5)
```

中心値を計算する関数を使用できます：

julia> schema((x=collect(1:10), ), Dict(:x => Center(median))) StatsModels.Schema with 1 entry:   x => x(centered: 5.5)

また、[`center`](@ref)は省略した場合、自動的に計算されます：

```
julia> schema((x=collect(1:10), ), Dict(:x => Center()))
StatsModels.Schema with 1 entry:
  x => center(x, 5.5)
```
