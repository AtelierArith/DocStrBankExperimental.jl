```
SummarizedExperiment()
```

空の `SummarizedExperiment` を作成します。アッセイはなく、行/列のアノテーションも空です。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> SummarizedExperiment()
0x0 SummarizedExperiment
  assays(0):
  rownames:
  rowdata(1): name
  colnames:
  coldata(1): name
  metadata(0):
```
