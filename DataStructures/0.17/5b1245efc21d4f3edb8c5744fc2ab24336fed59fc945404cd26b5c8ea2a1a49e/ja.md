```
sc[st] = v
```

もし `st` がセミトークンであり、`sc` が SortedDict または SortedMultiDict である場合、`sc[st]` は完全トークン `(sc,st)` が指す (キー, 値) ペアの値フィールドを参照します。この式は代入文のどちら側にも出現する可能性があります。時間: O(1)
