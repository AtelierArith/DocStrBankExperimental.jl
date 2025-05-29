```
dropunused!(x; samples = true, experiments = true, colnames = true, mapping = true)
```

`MultiAssayExperiment` `x` から未使用のサンプル、実験、および/または列名を削除します。修正された `x` への参照が返されます。

`samples = true` の場合、`sampledata(x)` はサンプルマッピングに存在するサンプルのみを保持するようにフィルタリングされます。

`experiments = true` の場合、`experiments(x)` はサンプルマッピングに存在する実験のみを保持するようにフィルタリングされます。

`colnames = true` の場合、`experiments(x)` の各エントリは、その実験のサンプルマッピングに存在する列名のみを保持するようにフィルタリングされます。

`mapping = true` の場合、サンプルマッピングは、`x` に存在しないサンプル、実験、または列名を含む行を削除するようにフィルタリングされます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> filtersamplemap!(x; experiments = "bar"); # 実験 'bar' のみを保持

julia> dropunused!(x) # 'foo' が削除されるのがわかります
MultiAssayExperiment object
  experiments(1): bar
  sampledata(2): name disease
  metadata(1): version
```
