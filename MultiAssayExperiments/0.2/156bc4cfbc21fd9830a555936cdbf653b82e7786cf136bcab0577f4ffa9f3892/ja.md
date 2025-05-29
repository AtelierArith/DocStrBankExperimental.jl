```
multifilter!(x; samples = nothing, experiments = nothing, colnames = nothing)
```

`MultiAssayExperiment` `x`を指定されたサンプル、実験、または列名のみを含むようにインプレースでフィルタリングします。これにより、変更された`x`への参照が返されます。

`samples`、`experiments`、および`colnames`の受け入れられる値については、[`filtersamplemap`](@ref)を参照してください。この関数の動作は、[`filtersamplemap!`](@ref)を呼び出した後に[`dropunused!`](@ref)を呼び出すのと同等です。`x`から削除される要素は引数によって異なります：

  * `samples != nothing`の場合、未使用のサンプルはサンプルデータから削除されます。
  * `experiments != nothing`の場合、未使用の実験は`experiments(x)`から削除されます。

これにより、フィルタリング後にゼロ列の実験がいくつか残る可能性がありますが、一般的には実験が通知なしに消えるよりも一貫した動作です。

  * `colnames != nothing`の場合、または`dropcolnames = true`かつ`samples != nothing`の場合、各実験から未使用の列が削除されます。

後者の条件は、サンプルに基づくフィルタリングが各実験の対応する列に伝播することが期待されるデフォルトの動作を提供します。これは、`dropcolnames = false`に設定することで無効にできます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> multifilter!(x; samples = ["Patient2", "Patient3"], experiments = "foo")
MultiAssayExperiment object
  experiments(1): foo
  sampledata(2): name disease
  metadata(1): version

julia> experiment(x)
100x6 SummarizedExperiment
  assays(3): foo bar whee
  rownames: Gene1 Gene2 ... Gene99 Gene100
  rowdata(2): name Type
  colnames: foo4 foo5 ... foo8 foo9
  coldata(3): name Treatment Response
  metadata(1): version
```
