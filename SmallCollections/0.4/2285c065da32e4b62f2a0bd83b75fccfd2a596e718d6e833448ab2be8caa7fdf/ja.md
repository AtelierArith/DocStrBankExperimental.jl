```
pop(d::AbstractSmallDict{N,K,V}, key, default::U) where {N,K,V,U} -> Tuple{SmallDict{N,K,V}, Union{V,U}}
```

もし `d` がキー `key` を持っている場合、それを削除し、新しい辞書と `d[key]` を返します。そうでない場合は、タプル `(SmallDict(d), default)` を返します。

また、`Base.pop!` も参照してください。
