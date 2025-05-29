```
layername(m::Meta)
```

The layer specified by `m`, as a `String`.

For example, `layer(GDSMeta(1, 2))` is `"GDS1_2"`, and `layername(SemanticMeta(:base))` is `"base"`.
