```julia
struct IP4 <: Identifier
```

  * `ip`**::String**
  * `port`**::UInt16**

`IPv4`は、インターネットプロトコルの「第4」版であり、インターネットサービスプロバイダー（ISP）とDHCP（ルーターサーバー）を介してコンピュータにIPアドレスを割り当てます。`Toolips`のIPは、アドレスが`String`である以外は、他の場所で見られる通りに書かれます。

```example
host = "127.0.0.1":8000
```

```julia
IP4(ip::Abstractstring, port::Integer)
```

  * 参照: `start!`, `Toolips`, `route`, `route!`
