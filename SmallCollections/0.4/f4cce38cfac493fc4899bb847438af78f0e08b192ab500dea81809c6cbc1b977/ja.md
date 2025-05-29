```
empty(d::AbstractSmallDict{N,K,V}) where {N,K,V,W} -> AbstractSmallVector{N,K,V}
empty(d::AbstractSmallDict{N,K,V}, W::Type) where {N,K,V,W} -> AbstractSmallVector{N,K,W}
empty(d::AbstractSmallDict{N,K,V}, L::Type, W::Type) where {N,K,V,L,W} -> AbstractSmallVector{N,L,W}
```

`d`と同じ容量の空の`AbstractSmallDictionary`を返し、`valtype`が`W`に、`keytype`が`L`に変更されます（指定されている場合）。結果の辞書は、`d`がそうである場合に限り、可変です。
