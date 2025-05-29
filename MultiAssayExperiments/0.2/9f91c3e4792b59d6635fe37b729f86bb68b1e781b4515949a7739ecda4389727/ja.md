```
experiment(x[, i]; sampledata = false)
```

`MultiAssayExperiment` `x` から指定された `SummarizedExperiment` を抽出します。`i` は `x` の実験の数を超えない正の整数、または希望する実験の名前を指定する文字列であることができます。`i` が指定されていない場合、デフォルトで `x` の最初の実験が使用されます。

`sampledata = true` の場合、`x` のサンプルデータを返される `SummarizedExperiment` の `coldata` に追加しようとします。これは、返される `SummarizedExperiment` の列にマッピングされるサンプルデータを基に `sampledata(x)` をサブセットすることによって行われます - 詳細については [`expandsampledata`](@ref) を参照してください。`sampledata(x)` と `SummarizedExperiment` の `coldata` に同じ名前だが異なる値を持つ列がある場合、前者は警告とともに省略されます。

`sampledata = true` の場合、返される `SummarizedExperiment` は `x` の関連する実験のコピーになります。`false` の場合、返されるオブジェクトは参照になります。

# 例

```jldoctest
julia> using MultiAssayExperiments;

julia> x = MultiAssayExperiments.exampleobject();

julia> experiment(x)
100x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene99 Gene100
  rowdata(2): name Type
  colnames: foo1 foo2 ... foo9 foo10
  coldata(3): name Treatment Response
  metadata(1): version

julia> experiment(x, 1); # 同じ結果

julia> experiment(x, "foo");

julia> experiment(x, "foo", sampledata = true) # サンプルデータを追加
100x10 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene99 Gene100
  rowdata(2): name Type
  colnames: foo1 foo2 ... foo9 foo10
  coldata(4): name Treatment Response disease
  metadata(1): version
```
