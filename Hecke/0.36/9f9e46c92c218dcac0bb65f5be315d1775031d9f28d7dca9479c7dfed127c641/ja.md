```
psubgroups(g::FinGenAbGroup, p::Integer;
           subtype = :all,
           quotype = :all,
           index = -1,
           order = -1)
```

特定の形式の$G$の部分群のイテレータを返します。`subtype`（および`quotype`）は、アーベル$p$-群としての部分群のタイプです。
