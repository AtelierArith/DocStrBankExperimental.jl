```julia
get_client_system(c::AbstractConnection) -> (::String, ::Bool)
```

`get_client_system` はクライアントのオペレーティングシステムを返します。もしそれが不明な場合（OpenBSDやそれに類似するもの）、`Toolips` はこれを `Linux` としてカウントします。`Function` は `String`（システム名）と `Bool`（これはモバイルオペレーティングシステムかどうか）を返します。

```julia
module ClientSystem
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    system, mobile = get_client_system(c)
    mobmsg = " not"
    if mobile
        mobmsg = ""
    end
    log(logger, system)
    write!(c, "you are$mobmsg on mobile, and your system is $system")
end
export home
end
```
