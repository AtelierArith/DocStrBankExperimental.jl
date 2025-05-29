```
MultiAssayExperiment(experiments)
```

`experiments`のセットから`MultiAssayExperiment`オブジェクトを作成します。サンプルごとの列データとサンプルマッピングは、すべての`experiments`からの列名の和集合から自動的に作成されます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> using SummarizedExperiments

julia> exp = OrderedDict{String, SummarizedExperiment}();

julia> exp["foo"] = SummarizedExperiments.exampleobject(100, 10);

julia> exp["bar"] = SummarizedExperiments.exampleobject(50, 20);

julia> out = MultiAssayExperiment(exp)
MultiAssayExperiment object
  experiments(2): foo bar
  sampledata(1): name
  metadata(0):
```
