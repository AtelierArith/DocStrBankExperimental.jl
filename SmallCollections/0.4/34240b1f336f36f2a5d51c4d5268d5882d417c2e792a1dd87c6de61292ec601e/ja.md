```
pop(d::AbstractSmallDict{N,K,V}) where {N,K,V} -> Tuple{SmallDict{N,K,V}, Pair{K,V}}
```

`d` からマッピング `key => val` を削除し、新しい辞書とマッピングを返します。辞書 `d` は空であってはなりません。

`Base.pop!` も参照してください。
