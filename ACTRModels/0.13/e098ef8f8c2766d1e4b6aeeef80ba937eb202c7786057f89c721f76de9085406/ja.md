```
find_indices(actr::ACTR; check_value = true, criteria...)
```

指定された基準に一致する最初のチャンクのインデックスを返します

# 引数

  * `actr`: ACTRオブジェクト
  * `criteria`: スロット-値ペアのためのキーワード引数のセット

# 例

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=:dog), Chunk(animal=cat)]
find_indices(chunks; animal=:dog)
```
