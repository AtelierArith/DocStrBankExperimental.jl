```
lookup(dat::DoubleArrayTrie, key::S) where S <: Union{AbstractString, AbstractVector{UInt8}}
```

トライ内で`key`を検索し、`0 <= id <= length(dat)`の範囲の一意のIDを返します。IDが0の場合、`key`はトライに存在しないことを意味します。
