```
setorder!(vi::VarInfo, vn::VarName, index::Int)
```

`vi`内の`vn`の`order`を`index`に設定します。ここで、`order`は`vn`のサンプリング前に実行される`observe`ステートメントの数です。
