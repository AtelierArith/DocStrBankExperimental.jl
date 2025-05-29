```
list_groups(species::String="";gn_url::String=gn_url())
```

`species`が指定されていない場合、GeneNetworkデータベースに表されているすべてのグループ（集団を分ける）を返します。`species`という文字列が指定されている場合、その種のすべてのグループを返します。
