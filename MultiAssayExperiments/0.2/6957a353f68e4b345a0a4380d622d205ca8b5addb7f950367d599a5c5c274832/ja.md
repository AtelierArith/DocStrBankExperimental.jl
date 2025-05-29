```
dropunused(x; kwargs...)
```

未使用のサンプル、実験、または列名が削除された新しい `MultiAssayExperiment` を返します。これは `x` のコピーを作成し、それを（および `kwargs` にある任意のキーワード引数を）[`dropunused!`](@ref) に渡します。詳細については後者の関数を参照してください。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = filtersamplemap(x; experiments = "bar"); # 実験 'bar' のみを保持

julia> dropunused(y) # 'foo' が削除されていることがわかります
MultiAssayExperiment object
  experiments(1): bar
  sampledata(2): name disease
  metadata(1): version
```
