```
find_indices(actr::ACTR, funs...; check_value=true, criteria...)
```

条件に一致する最初のチャンクのインデックスを返します

# 引数

  * `actr`: ACTRオブジェクト
  * `funs`: 一連の関数

# キーワード

  * `check_value=true`:
  * `criteria`: スロット-値ペアのためのキーワード引数のセット

# 例

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=:dog), Chunk(animal=cat)]
find_indices(chunks; animal=:dog)
```
