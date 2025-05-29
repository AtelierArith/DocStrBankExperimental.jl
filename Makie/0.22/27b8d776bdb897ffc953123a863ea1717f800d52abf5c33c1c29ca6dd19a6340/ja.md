```
broadcast_foreach(f, args...)
```

broadcastと同様ですが、foreach用です。形状を気にせず、タプルやStaticVectorsをスカラーとして扱います。このメソッドは、スカラーまたはベクトル/配列形式を持つ属性に対してブロードキャストするためのものです。例としては、異なるサイズを持つが単一の色の散布マーカーのコレクションが挙げられます。属性の長さは`attr_broadcast_length`で決定され、要素には`attr_broadcast_getindex`でアクセスされます。
