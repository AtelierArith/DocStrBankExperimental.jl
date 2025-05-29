```
call(lk::Link, [from::Link,] args2...; timeout::Real=5.0)
call(name::Symbol, ....)
```

アクターを呼び出してその動作を実行し、結果を含む [`Response`](@ref) を送信します。

# 引数

  * アクター `lk::Link`（または登録されている場合は `name::Symbol`）,
  * `from::Link`: 送信者リンク,
  * `args2...`: アクターへの残りの引数.
  * `timeout::Real=5.0`: タイムアウト（秒単位）。

**注意:** `from` が省略された場合、`call` はブロックされ、結果を返します。
