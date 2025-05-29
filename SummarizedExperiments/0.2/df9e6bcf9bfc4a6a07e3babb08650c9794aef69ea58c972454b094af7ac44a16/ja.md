```
SummarizedExperiment(assays)
```

提供されたアッセイを使用して `SummarizedExperiment` のインスタンスを作成します。

`assays` のすべてのエントリは、最初の2次元の範囲が同じである必要があります。ただし、それ以外の次元は任意の数を持つことができます。各アッセイは異なるタイプであることができます。`assays` には少なくとも1つのアッセイ行列が含まれている必要があります。

`coldata` と `rowdata` には、すべての `nothing` を含む `"name"` 列を持つ空の `DataFrame` が作成されます。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> assays = OrderedDict{String, AbstractArray}(
          "foobar" => [[1,2] [3,4] [5,6]], 
          "whee" => [[1.2,2.3] [3.4,4.5] [5.6,7.8]]);

julia> x = SummarizedExperiment(assays)
2x3 SummarizedExperiment
  assays(2): foobar whee
  rownames:
  rowdata(1): name
  colnames:
  coldata(1): name
  metadata(0):
```
