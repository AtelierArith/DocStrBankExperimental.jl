```julia
abstract type AbstractConnection
```

`AbstractConnection`は、サーバーが各クライアントと個別に相互作用する方法です。`Connection`のバリエーションは、ルートに唯一の引数として渡されます。`Connection`

  * `write!`で書き込むことができます
  * `get_ip`のような*ゲッター*関数を使用してアクセスできるクライアントデータを含みます
  * 参照: `start!`, `route`, `route!`, `Connection`, `get_ip`, `get_args`
