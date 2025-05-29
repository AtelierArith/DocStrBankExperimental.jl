```
terminate!(entity::AbstractEntity)
```

エンティティの `is_terminated` フラグを `true` に設定し、エンティティとのすべてのサブスクリプションを切断することでエンティティを終了します。

# 引数

  * `entity::AbstractEntity`: 終了するエンティティ。
