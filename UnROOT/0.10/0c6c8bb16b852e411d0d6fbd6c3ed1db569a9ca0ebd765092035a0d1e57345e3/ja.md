```
function LazyTree(f::ROOTFile, tree::TTree, treepath, branches; sink = LazyTree)
```

選択したブランチのみの遅延ツリーオブジェクトを作成します。`branches`は`String`、`Regex`、または`Pair{Regex, SubstitutionString}`のベクターであり、最初のアイテムは正規表現セレクタで、2番目のアイテムはリネームパターンです。代替のコンテナは、シンク関数を提供することで使用できます。シンク関数は、Tables.jlインターフェースを持つテーブルを引数として受け取る必要があります。テーブルの列はLazyBranchオブジェクトで埋められます。
