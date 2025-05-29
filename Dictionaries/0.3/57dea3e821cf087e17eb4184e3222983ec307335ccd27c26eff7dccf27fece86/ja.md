```
unset!(indices::AbstractIndices, i)
```

インデックス `i` が `indices` に存在する場合は削除し、そうでなければ何もしません。

```
unset!(dict::AbstractDictionary, i)
```

インデックス `i` が `dict` に存在する場合は削除し、そうでなければ何もしません。

関連: `delete!`, `set!`.
