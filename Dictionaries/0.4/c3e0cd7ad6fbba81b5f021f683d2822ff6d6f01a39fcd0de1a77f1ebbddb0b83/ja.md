```
delete!(indices::AbstractIndices, i)
```

インデックス `i` を `indices` から削除します。`i` が存在しない場合はエラーが発生します。

```
delete!(dict::AbstractDictionary, i)
```

インデックス `i` を `dict` から削除します。`i` が存在しない場合はエラーが発生します。

関連: `unset!`, `insert!`.
