```
is_subscribed(subject::AbstractEntity, target::AbstractEntity)
```

`subject`が`target`にサブスクライブされているかを確認します。

# 引数

  * `subject::AbstractEntity`: `target`にサブスクライブされている可能性のあるエンティティ。
  * `target::AbstractEntity`: `subject`にサブスクライブされている可能性のあるエンティティ。

# 戻り値

`subject`が`target`にサブスクライブされている場合は`true`、そうでない場合は`false`を返します。
