```
setsamplemap!(x, value)
```

`MultiAssayExperiment` `x` のサンプルマッピングを `DataFrame` `value` に設定します。これにより、変更された `x` への参照が返されます。

`value` には、`sample`、`experiment`、`colname` の列がその順序で含まれている必要があります。各列には文字列のベクトルが含まれている必要があります：

  * `sample` の値は、`sampledata(x)` のサンプル名に対応する場合があります（ただし、必須ではありません）。
  * `experiment` の値は、`experiments(x)` のキーに対応する場合があります（ただし、必須ではありません）。
  * `colname` の値は、同じ行の `experiment` にある対応する `SummarizedExperiment` の列に対応する必要があります（ただし、必須ではありません）。

この対応関係は、便利なサブセット化や抽出に使用されます。例えば、[`expandsampledata`](@ref)、[`filtersamplemap`](@ref) などです。ただし、サンプルマッピング列の値は、対応するターゲットと1:1で一致する必要はありません。片方にのみ固有の値は、関連するメソッドで無視されます。これにより、ユーザーは常に有効性チェックに引っかかることなく、オブジェクトを柔軟に操作できます。

特定の `experiment` と `colname` の組み合わせが複数回発生することは合法ですが（非常に珍しいですが）、これにより [`expandsampledata`](@ref) のようなメソッドで警告が発生する可能性があります。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = samplemap(x)[1:10,:];

julia> setsamplemap!(x, y);

julia> size(samplemap(x))[1]
10
```
