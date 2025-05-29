```
writeframe(io, trcs, hdrs)
```

`io::JSeis`に対応するJavaSeisデータセットにデータのフレームを書き込みます。`trcs`と`hdrs`は2次元配列です。書き込まれるデータセットの位置は、`hdrs`に保存されたフレームワークヘッダーの値によって決まります。
