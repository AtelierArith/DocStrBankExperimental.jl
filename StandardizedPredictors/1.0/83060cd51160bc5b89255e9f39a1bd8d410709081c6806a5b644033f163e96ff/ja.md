```
struct ZScore
```

zスコアリングスキームを表します。`StatsModels.AbstractContrasts`に似ています。`Dict`内の値として`schema`へのヒントとして渡すか、`fit`の`contrasts`キーワード引数として渡します。

## 例

使用する中心値とスケール値を指定できます：

```
julia> schema((x=collect(1:10), ), Dict(:x => ZScore(; center=5, scale=3)))
StatsModels.Schema with 1 entry:
  x => x(centered: 5 scaled: 3)
```

また、スケールを省略すると自動的に計算されます：

```
julia> schema((x=collect(1:10), ), Dict(:x => ZScore()))
StatsModels.Schema with 1 entry:
  x => x(centered: 5.5 scaled: 3.03)
```
