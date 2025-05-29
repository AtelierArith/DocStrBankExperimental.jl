```
getfiles(X)
```

ファイルのようなエントリ（通常のファイルまたはファイルへのシンボリックリンク）のみをフィルタリングします。その後、すべてのシンボリックリンクをたどります。結果は `FileEntry` のみです。

`X |> filter(isfile) |> map(follow)` のショートカットです（カリー化のために `import CommandLiner.Iter.Hack: filter, map` を使用）。
