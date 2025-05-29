```
struct CachedMethodTable <: MethodTableView
```

別のメソッドテーブルビューの上に、元のメソッドテーブルよりも繰り返し同じクエリに対して迅速に応答できる追加のローカルファストパスキャッシュを重ねます。
