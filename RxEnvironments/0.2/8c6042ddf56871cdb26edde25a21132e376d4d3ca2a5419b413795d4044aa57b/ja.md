```
update!(e::AbstractEntity{T,ContinuousEntity,E}) where {T,E}
```

エンティティ `e` の現在の状態と最後の更新から経過した時間に基づいて、エンティティの状態を更新します。状態遷移関数として機能します。

# 引数

  * `e::AbstractEntity{T,ContinuousEntity,E}`: 更新するエンティティ。
