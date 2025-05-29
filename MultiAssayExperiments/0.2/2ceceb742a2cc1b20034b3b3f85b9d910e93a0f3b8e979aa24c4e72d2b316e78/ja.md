```
sampledata(x, check = true)
```

`MultiAssayExperiment` `x`のサンプルデータを含む`DataFrame`を返します。

返されるオブジェクトは、最初の列にユニークな文字列のベクターを含む`name`を含む必要があります。`check = true`の場合、関数は返す前にサンプルデータの有効性をチェックします。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> names(sampledata(x))
2-element Vector{String}:
 "name"
 "disease"
```
