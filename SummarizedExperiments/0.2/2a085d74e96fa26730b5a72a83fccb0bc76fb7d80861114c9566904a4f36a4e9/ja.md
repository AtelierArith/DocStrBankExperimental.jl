```
setassays!(x, value)
```

`x`のアッセイを`value`に設定します。`value`は、キーがアッセイ名で、値が配列である`OrderedDict`です。`value`内のすべての配列は、最初の2次元に対して`x`と同じサイズである必要があります。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> length(assays(x))
3

julia> refresh = copy(assays(x));

julia> delete!(refresh, "foo");

julia> setassays!(x, refresh)

julia> length(assays(x))
2
```
