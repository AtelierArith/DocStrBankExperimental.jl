```
is_povm_element(M :: AbstractMatrix; atol=ATOL :: Float64) :: Bool
```

行列 `M` が以下の制約を満たす場合、`true` を返します：

  * `M` はエルミート行列である
  * `M` は非負定値である
