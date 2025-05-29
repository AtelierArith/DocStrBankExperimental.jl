```
setcoldata!(x, value)
```

`x`の列注釈を`value`に設定します。

`value`が`DataFrame`の場合、最初の列は`"name"`と呼ばれ、`x`の列名を含む必要があります。これは`Vector{String}`または（列名が利用できない場合）`Vector{Nothing}`である可能性があります。

`value`が`nothing`の場合、これは`nothing`を含む1つの`"name"`列を持つ`DataFrame`と同等と見なされます。

返り値は変更された`x`への参照です。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> replacement = copy(coldata(x));

julia> replacement[!,"foobar"] = [ rand() for i in 1:size(x)[2] ];

julia> setcoldata!(x, replacement);

julia> names(coldata(x))
4-element Vector{String}:
 "name"
 "Treatment"
 "Response"
 "foobar"
```
