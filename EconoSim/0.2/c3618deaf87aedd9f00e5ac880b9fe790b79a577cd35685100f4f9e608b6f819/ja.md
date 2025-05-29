```
Actor - 経済的なアクターを代表するエージェント。
```

# フィールド

  * id::Int - エージェントのID。
  * types::Set{Symbol} - アクターのタイプ。タイプはデータ収集や行動関数で使用されることを意図しています。
  * model*behaviors::Vector{Function} - econo*model*step!によって呼び出される関数のリストで、これはデフォルトのmodel*step!関数です。
  * behaviors::Vector{Function} - アクターがアクティブ化されたときに呼び出される行動関数のリスト。
  * balance::Balance - エージェントのバランスシート。
  * posessions::Entities - エージェントが個人的に所有しているエンティティ。
  * stock::Stock - エージェントが保有するストック。ストックはビジネス目的で使用されると考えられています。
  * producers::Set{Producer} - エージェントの生産施設。
  * prices::D where D <: Dict{<:Blueprint, Price} - アクターが販売する製品の価格。
  * properties::Dict{Symbol, Any} - 内部使用のため。

作成後、アクターに任意のフィールドを設定することができ、構造の一部でないものも含まれます。これは、特定の状態をアクターと共に保存する必要がある場合に便利です。
