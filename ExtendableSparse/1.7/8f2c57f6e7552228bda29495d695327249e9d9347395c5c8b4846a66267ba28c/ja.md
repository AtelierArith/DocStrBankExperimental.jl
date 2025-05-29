```
allow_views(::preconditioner_type)
```

ブロック前処理器内の行列パーティションに対する因子分解は、配列ビューで動作する場合としない場合があります。例えば、umfpack因子分解はビューで動作しませんが、ILUZeroPreconditionerは動作します。`allow_views`のメソッドを実装して`false`または`true`を返すことで、適切なケースにディスパッチすることができます。
