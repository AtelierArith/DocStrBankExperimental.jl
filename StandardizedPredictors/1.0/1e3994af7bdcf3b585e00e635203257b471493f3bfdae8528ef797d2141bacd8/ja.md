```
struct Scale
```

スケーリングスキームを表し、`StatsModels.AbstractContrasts`に似ています。`Dict`内の値として`schema`へのヒントとして渡すか、`fit`の`contrasts`キーワード引数として渡します。

## 例

使用するスケール値を指定できます：

```
julia> schema((x=collect(1:10), ), Dict(:x => Scale(5)))
StatsModels.Schema with 1 entry:
  x => x(scaled: 5))
```

スケール値を計算するために関数を使用できます：

```
julia> schema((x=collect(1:10), ), Dict(:x => Scale(mad))) 
StatsModels.Schema with 1 entry:   
  x => x(scaled: 3.71)
```

または、[`scale`](@ref)は省略した場合に自動的に計算されます：

```
julia> schema((x=collect(1:10), ), Dict(:x => Scale()))
StatsModels.Schema with 1 entry:
  x => x(scaled: 3.03)
```
