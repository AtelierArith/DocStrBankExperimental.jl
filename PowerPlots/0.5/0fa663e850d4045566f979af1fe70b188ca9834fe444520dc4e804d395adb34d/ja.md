```
`powerplot(
    case::Dict{String,<:Any};
    layout_algorithm=kamada_kawai,
    edge_components=[:branch],
    node_components=[:bus],
    connected_components=[:gen,:load],
    fixed=false,
    kwargs...)`
```

プラワープロットを作成します。kwargオプションに関するドキュメントはGitHubリポジトリを確認してください。
