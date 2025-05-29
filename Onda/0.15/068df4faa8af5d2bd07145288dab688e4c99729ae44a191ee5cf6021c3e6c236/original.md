```
validate_annotations(annotations)
```

Perform both table-level and row-level validation checks on the content of `annotations`, a presumed `onda.annotation` table. Returns `annotations`.

This function will throw an error in any of the following cases:

  * `Legolas.validate(Tables.schema(annotations), AnnotationV1SchemaVersion())` throws an error
  * `AnnotationV1(r)` errors for any `r` in `Tables.rows(annotations)`
  * `annotations` contains rows with duplicate `id`s
