```
find_index(chunks::Array{<:Chunk,1}, funs...; check_value=true, criteria...)
```

条件に一致する最初のチャンクのインデックスを返します

# 引数

  * `chunks`: チャンクの配列
  * `funs`: 関数のセット
  * `criteria`: スロット-値ペアのためのキーワード引数のセット

# キーワード

  * `check_value=true`:
  * `criteria`: スロット-値ペアのためのキーワード引数のセット

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=cat)]
find_index(chunks; animal=:dog)
```
