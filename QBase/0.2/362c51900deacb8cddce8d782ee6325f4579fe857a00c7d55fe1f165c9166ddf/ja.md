```
is_unitary( U :: Matrix; atol=ATOL :: Float64 ) :: Bool
```

行列 `U` がユニタリである場合は `true` を返します。ユニタリ行列のエルミート随伴はその逆行列です：

  * `U' * U == I` ここで `I` は単位行列です。
