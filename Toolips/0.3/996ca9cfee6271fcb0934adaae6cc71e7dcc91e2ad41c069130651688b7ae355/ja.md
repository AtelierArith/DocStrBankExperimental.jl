```julia
Connection <: AbstractConnection
```

  * `stream`**::HTTP.Stream**
  * `data`**::Dict{Symbol, Any}**
  * `routes`**::Vector{<:AbstractRoute}**

`Connection`は、`Toolips`サーバーが受信したHTTPリクエストを処理するために使用する主要な型です。`Connection`をインデックスすると、`String`または`Symbol`が使用された場合にルートまたはサーバーデータが得られます。`Connection`は`write!`を使って書き込むこともできます。引数やその他のクライアント情報は、`AbstractConnection`のさまざまな*get*関数を使用して取得できます。

```julia
get_args(c::AbstractConnection)
get_ip(c::AbstractConnection)
get_post(c::AbstractConnection)
get_route(c::AbstractConnection)
get_method(c::AbstractConnection)
get_parent(c::AbstractConnection)
get_client_system(c::AbstractConnection)
```

```julia
proxy_pass!(c::Connection, url::String)
```

`Connection`は、ルートのハンドラー`Function`に唯一の引数として直接提供されます。`route`で`Route`を作成すると、`Connection`が渡され、それを`write!`で使用して応答することができます。

```example
module SampleServer
using Toolips
        # 注釈を付けることでルートに対して複数のディスパッチが可能になります（推奨）
home = route("/") do c::Connection
    write!(c, "hello world!")
end

export home, start!
end
```

`Servables`も`write!`にバインドされているため、`Connection`は`Components`を簡単に提供できます。

  * 参照: `route`, `AbstractConnection`, `route!`, `write!`, `Components`, `IOConnection`, `MobileConnection`
