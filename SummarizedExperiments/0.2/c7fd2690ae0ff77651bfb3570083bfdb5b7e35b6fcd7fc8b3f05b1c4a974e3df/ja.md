```
setassay!(x[, i], value)
```

`x`の要求されたアッセイを任意の配列のような`value`に設定します。`value`の最初の2つの次元は、`x`の次元と等しい必要があります。

`i`はインデックスを指定する整数である場合、正の値であり、`length(assays(x))`を超えてはいけません。または、名前を含む文字列である場合、既存の名前または新しい名前である可能性があります。`i`が指定されていない場合、`value`は`x`の最初のアッセイとして設定されます。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> first_sum = sum(assay(x));

julia> second_sum = sum(assay(x, 2));

julia> setassay!(x, assay(x, 2)); # 2番目のアッセイで最初のアッセイを置き換えます。

julia> first_sum == sum(assay(x))
false

julia> second_sum == sum(assay(x))
true

julia> setassay!(x, 1, assay(x, 2)); # 上記のより明示的な形式。

julia> setassay!(x, "foo", assay(x, 2));
```
