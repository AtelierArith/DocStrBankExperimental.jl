```
get_mesh_entity_tag(met::JutulMesh, entity::JutulEntity, tag_group::Symbol, tag_value = missing; throw = true)
```

Get the indices tagged for `entity` in group `tag_group`, optionally for the specific `tag_value`. If `ismissing(tag_value)`, the Dict containing the tag group will be returned.
