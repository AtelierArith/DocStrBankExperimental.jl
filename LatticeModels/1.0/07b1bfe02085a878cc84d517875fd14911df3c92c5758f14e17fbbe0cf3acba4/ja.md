```
currentsfromto(currents, src[, dst])
```

`src`から`dst`領域への合計電流を見つけます。`dst`が指定されていない場合、`src`から他のすべてのサイトへの電流が返されます。

## 引数

  * `currents`: 処理する`AbstractCurrents`オブジェクト。
  * `src`: ソース領域。
  * `dst`: 宛先領域。

`src`と`dst`は、サイト/サイトのコレクションまたは`LatticeValue{Bool}`マスクであることができます。
