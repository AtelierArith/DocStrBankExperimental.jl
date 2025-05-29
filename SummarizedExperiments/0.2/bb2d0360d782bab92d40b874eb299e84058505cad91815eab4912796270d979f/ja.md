```
setrowdata!(x, value)
```

`x`の行注釈を`value`に設定します。

`value`が`DataFrame`の場合、最初の列は`"name"`と呼ばれ、`x`の行名を含む必要があります。これは`AbstractVector{AbstractString}`または`Vector{Nothing}`（行名が利用できない場合）である必要があります。

`value`が`nothing`の場合、これは`nothing`を含む1つの`"name"`列を持つ`DataFrame`と同等と見なされます。

返り値は変更された`x`への参照です。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> # DataFramesを使用

julia> replacement = copy(rowdata(x));

julia> replacement[!,"foobar"] = [ rand() for i in 1:size(x)[1] ];

julia> setrowdata!(x, replacement);

julia> names(rowdata(x))
3-element Vector{String}:
 "name"
 "Type"
 "foobar"
```
