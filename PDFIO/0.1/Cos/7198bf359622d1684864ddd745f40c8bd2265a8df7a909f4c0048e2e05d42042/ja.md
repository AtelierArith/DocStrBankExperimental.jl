```
    cosDocClose(doc::CosDoc)
```

`CosDoc`によって消費されたすべてのシステムリソースを回収します。このメソッドが呼び出された後は、`CosDoc`を使用してはいけません。`cosDocClose`は、ドキュメントを'cosDocOpen'で開いた場合にのみ明示的に呼び出す必要があります。`pdDocOpen`で開かれたドキュメントは、このメソッドを使用する必要はありません。
