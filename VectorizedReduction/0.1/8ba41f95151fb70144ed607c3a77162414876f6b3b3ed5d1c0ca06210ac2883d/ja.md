```
vvmaximum(f, A; dims=:, init=typemin)
```

`f`の各要素に対して`A`の最大値を計算します。指定された`dims`にわたって、最大値は`init`で初期化されます。`init`は`<:Number`の値または単一の型引数を受け入れる関数である可能性があります。
