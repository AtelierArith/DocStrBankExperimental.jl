```
samplemap(x)
```

`MultiAssayExperiment` `x`からサンプルマッピングを含む順序付き辞書を返します。

返されるオブジェクトは、`sample`、`experiment`、`colname`の順に列を含む必要があります。各列は文字列のベクトルを含み、行は一意である必要があります。`check = true`の場合、関数は返す前にサンプルデータの有効性をチェックします。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> names(samplemap(x))
3-element Vector{String}:
 "sample"
 "experiment"
 "colname"
```
