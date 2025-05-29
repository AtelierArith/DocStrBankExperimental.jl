```
sentinelview(X, I, [sentinel=nothing])
```

`view(X, I)`と同様ですが、`sentinel`を伝播します。

# 例

```julia
A = [10, 20, 30]

Av = sentinelview(A, [1, 2, 3])  # view(A, [1, 2, 3])と同等
Av == [10, 20, 30]

Av = sentinelview(A, [1, nothing, 3])  # インデックスのnothingを結果に伝播
Av == [10, nothing, 30]
```
