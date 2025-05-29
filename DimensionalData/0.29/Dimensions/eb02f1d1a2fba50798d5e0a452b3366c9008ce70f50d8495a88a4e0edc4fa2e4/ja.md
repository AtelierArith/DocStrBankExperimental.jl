```
rebuild(dim::Dimension, val) => Dimension
rebuild(dim::Dimension; val=val(dim)) => Dimension
```

`dim`のフィールドと渡された新しいフィールドを使って`dim`を再構築します。
