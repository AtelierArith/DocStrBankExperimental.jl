```
create_entity(entity; is_discrete = false, is_active = false, real_time_factor = 1)
```

指定されたエンティティを装飾する `RxEntity` を作成します。`is_discrete` および `is_active` パラメータは、エンティティが離散状態空間または連続状態空間に存在するかどうか、またエンティティがアクティブかパッシブかを決定します。`real_time_factor` パラメータは、エンティティの時計がどれだけ速く進むかを決定します。この関数は、より複雑なエンティティのネットワークを作成するための低レベルのAPIとして使用できます。
