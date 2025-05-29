```
delete(r::RemoteConcept{<:AbstractThingType})
```

データベースからタイプを削除するには、そのタイプをトランザクションと共にRemoteConceptにパッケージ化します。このタイプに基づくEntity、Attribute、またはRelationがデータベースに存在しない場合にのみ、タイプを削除できることに注意してください。
