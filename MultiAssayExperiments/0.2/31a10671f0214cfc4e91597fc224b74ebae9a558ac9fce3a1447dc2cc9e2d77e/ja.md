```
setsampledata!(x, value)
```

`MultiAssayExperiment` `x` のサンプルデータを `DataFrame` `value` に設定します。

返されるオブジェクトは、最初の列にユニークな文字列のベクターを含む `name` を含む必要があります。`check = true` の場合、関数は返す前にサンプルデータの有効性をチェックします。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> sd = copy(sampledata(x));

julia> sd[!,"stuff"] = [rand() for i in 1:size(sd)[1]];

julia> setsampledata!(x, sd);

julia> names(sampledata(x))
3-element Vector{String}:
 "name"
 "disease"
 "stuff"
```
