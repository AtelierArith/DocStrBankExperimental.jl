```
getknnresult(k::Integer, ctx::AbstractContext) -> KnnResult
```

同じスレッドの共有結果セットを取得し、メモリ割り当てを回避するための汎用関数。この関数は、共有結果や特別な方法でスレッドを使用するインデックスやキャッシュに対して特化されるべきです。
