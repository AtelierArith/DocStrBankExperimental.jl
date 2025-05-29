```
getcell(meta::MetaVLSV, location:::AbstractVector{<:AbstractFloat}) -> Int
```

与えられた空間の `location`（メートル単位）を含むセルIDを返します。ドメイン境界は除外されます。3Dの位置のみを受け付けます。
