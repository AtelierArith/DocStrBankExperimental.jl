```
exampleobject(nrow, ncol)
```

指定された行数と列数を持つ例の `SummarizedExperiment` オブジェクトを作成します。これは、例やテストの簡潔さを向上させるために使用されます。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10)
20x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene19 Gene20
  rowdata(2): name Type
  colnames: Patient1 Patient2 ... Patient9 Patient10
  coldata(3): name Treatment Response
  metadata(1): version
```
