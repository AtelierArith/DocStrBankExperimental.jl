```
broadcast_foreach(f, args...)
```

broadcastと同様ですが、foreach用です。形状を気にせず、タプルやStaticVectorsをスカラーとして扱います。このメソッドは、スカラーまたはベクトル/配列形式を持つ属性に対してブロードキャストするためのものです。例としては、異なるサイズを持つ散布マーカーのコレクションがあり、色は単一である場合が挙げられます。属性の長さは`attr_broadcast_length`で決定され、要素は`attr_broadcast_getindex`でアクセスされます。
