```
default_buffer() -> SlabBuffer{1048576}
```

現在のタスクローカルのデフォルト `SlabBuffer` を返します。現在のタスクに存在しない場合は、自動的に作成されます。これは現在 `SlabBuffer{1048576}` のみで機能し、作成されるスラブサイズを調整することはできません。
