```
Field(location, path, name, iter;
      grid = nothing,
      architecture = nothing,
      indices = (:, :, :),
      boundary_conditions = nothing,
      reader_kw = NamedTuple())
```

`path`に保存された`name`というフィールドを`iter`回目で読み込みます。指定がない限り、`grid`は`path`から読み込まれます。
