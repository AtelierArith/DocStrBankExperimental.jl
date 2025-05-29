```
get_mesh_entity_tag(met::JutulMesh, entity::JutulEntity, tag_group::Symbol, tag_value = missing; throw = true)
```

`tag_group`内の`entity`にタグ付けされたインデックスを取得し、オプションで特定の`tag_value`について取得します。`tag_value`が`ismissing`の場合、タググループを含むDictが返されます。
