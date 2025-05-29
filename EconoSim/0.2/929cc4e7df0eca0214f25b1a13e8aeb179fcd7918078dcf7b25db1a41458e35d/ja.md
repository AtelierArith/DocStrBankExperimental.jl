```
Actor - 汎用アクターの作成関数。
```

# パラメータ

  * id::Int = ID_COUNTER - エージェントのID。IDが指定されていない場合、標準のIDのシーケンスが使用されます。標準のシーケンスとユーザー定義のIDを混在させることは推奨されません。
  * type::Union{Symbol, Nothing} = nothing - アクターのタイプ。タイプはデータ収集および/または行動関数で使用されることを意図しています。
  * model*behavior::Union{Function, Nothing} = nothing - econo*model*step!によって呼び出されるデフォルト関数で、これはデフォルトのmodel*step!関数です。
  * behavior::Union{Function, Nothing} = nothing - アクターがアクティブ化されたときに呼び出されるデフォルトの行動関数です。
  * balance::Balance = Balance() - エージェントのバランスシート。
  * posessions::Entities = Entities() - エージェントが個人的に所有しているエンティティ。
  * stock::Stock = Stock() - エージェントが保有する在庫。在庫はビジネス目的で使用されると見なされます。
  * producers::Union{AbstractVector{Producer}, AbstractSet{Producer}} = Set{Producer}() - エージェントの生産施設。
