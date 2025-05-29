```
MultiAssayExperiments.exampleobject()
```

例の `MultiAssayExperiment` オブジェクトを作成します。これは、例やテストの簡潔さを向上させるために使用されます。

# 例

```jldoctest
julia> using MultiAssayExperiments 

julia> x = MultiAssayExperiments.exampleobject()
MultiAssayExperiment object
  experiments(2): foo bar
  sampledata(2): name disease
  metadata(1): version
```
