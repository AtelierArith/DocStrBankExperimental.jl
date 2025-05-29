```
Provenance(object, [sigtype=NoSignature()])
```

`object`に関連付けられた出所データをキャプチャし、タイムスタンプを付けます。これは`object`の型に対する`provenance`定義によって定義されます。

`object`に関連する出所データをキャプチャしたい出所追跡パッケージによって呼び出されます。`sigtype`を渡すことで、生成された出所データの署名をカスタマイズできます。
