```
augment(term) -> Vector{String}
```

与えられた用語に対して、同義語として扱うべき用語のリストを返します。現在は、（スペース、ハイフン）を（スペースなし）で拡張することのみをサポートしています。

## 例

```jldoctest
julia> KeywordSearch.augment("arctic wolf")
2-element Vector{String}:
 "arctic wolf"
 "arcticwolf"
 
```
