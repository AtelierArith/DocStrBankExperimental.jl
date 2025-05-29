```
deserialize_lpcm_callback(format::AbstractLPCMFormat, samples_offset, samples_count)
```

`(callback, required_byte_offset, required_byte_count)`を返します。ここで、`callback`は`required_byte_offset`と`required_byte_count`で指定されたバイトブロックを受け取り、`samples_offset`と`samples_count`で指定されたサンプルを返します。

フォールバックとして、この関数は`(callback, missing, missing)`を返します。ここで、`callback`は利用可能なすべてのバイトを要求します。部分的/ブロックベースのデシリアライズをサポートする`AbstractLPCMFormat`のサブタイプ（例えば、基本的な`LPCMFormat`）は、この関数をオーバーロードして、呼び出し元が要求したサンプル範囲に必要なバイト範囲だけを正確に要求することができます。

これにより、呼び出し元はバイトブロックの取得を自分で処理できる一方で、OndaのLPCMシリアライズAPIは呼び出し元のストレージレイヤーの選択に対して無関係になります。
