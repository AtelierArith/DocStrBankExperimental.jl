```
find_index(chunks::Array{<:Chunk,1}; check_value=true, criteria...)
```

条件に一致する最初のチャンクのインデックスを返します

# 引数

  * `chunks`: チャンクの配列

# キーワード

  * `check_value=true`:
  * `criteria`: スロット-値ペアのためのキーワード引数のセット

# 例

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=cat)]
find_index(chunks; animal=:dog)
```
