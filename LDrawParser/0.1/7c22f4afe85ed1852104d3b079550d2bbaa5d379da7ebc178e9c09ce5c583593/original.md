```
populate_part_geometry!(model,frontier=Set(collect(part_keys(model))))
```

Load all geometry into `model.parts`. Loading is recursive, so that geometry will be loaded through arbitrary levels of nested subparts until finally being stored in each atomic part that is referenced by the main model(s).
