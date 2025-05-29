```
subscribe_to_observations!(entity::AbstractEntity, actor)
```

Subscribe `actor` to the observations of `entity`. Any data sent to `entity` will be received by `actor` after this function is called.
