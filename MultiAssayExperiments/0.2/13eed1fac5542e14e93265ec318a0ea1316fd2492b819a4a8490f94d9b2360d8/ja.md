```
multifilter!(x; samples = nothing, experiments = nothing, colnames = nothing)
```

指定されたサンプル、実験、または列名のみをフィルタリングした新しい `MultiAssayExperiment` を返します。これは `x` のコピーを作成し、それを（および `kwargs` の任意のキーワード引数を）[`multifilter!`](@ref) に渡します。詳細については後者の関数を参照してください。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> multifilter(x; samples = ["Patient2", "Patient3"], experiments = "foo")
MultiAssayExperiment object
  experiments(1): foo
  sampledata(2): name disease
  metadata(1): version
```
