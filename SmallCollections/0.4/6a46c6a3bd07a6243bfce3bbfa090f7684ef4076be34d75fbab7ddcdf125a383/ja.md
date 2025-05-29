```
invget(d::AbstractSmallDict{N,K}, val, default::T) where {N,K,T} -> Union{K,T}
```

`d`の値が`val`と等しい（`isequal`の意味で）キーを返します。該当するキーがない場合は`default`を返します。

この逆引きは、キーによる「前方」検索と同じくらい速いです。返されるキーは、`keys(d)`の中で最初に一致するものです。
