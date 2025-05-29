```
is_povm( Π :: Vector; atol=ATOL :: Float64 ) :: Bool
```

`Π`が以下の制約を満たす場合に`true`を返します。

  * POVMが完全である: `sum(Π) == I`
  * 各POVM要素はエルミートである
  * 各POVM要素は正半定である
