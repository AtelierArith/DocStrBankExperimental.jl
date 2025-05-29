```
@mime_type "type"
```

Registers `"type"` as a `MIME` type registered with this package at package definition time. Future calls to `@custom_tile` and `@pprint` with no provided `mime_types` arguments will generate methods corresponding to this type, along with previously declared mime types.
