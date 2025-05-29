```julia
get_cookies(c::AbstractConnection) -> ::Vector{Cookie}
```

指定された `Connection` からクッキーを取得します。これらのクッキーは `respond!` を使用して保存できます。詳細はこの関数とともに `Toolips.respond!` および `Toolips.Cookie` を参照してください。

```example
module CookieServer
using Dates
using Toolips

main = route("c") do c::AbstractConnection
    cookies = get_cookies(c)
    if length(cookies) == 0
        cookie = Toolips.Cookie(
            name = "session_id",
            value = "abc123",
            path = "/",
            httponly = true,
            expires = now() + Day(1)  # クッキーは1日後に期限切れになります)
                                    # (必ず `Vector{Cookie}` である必要があります)
        respond!(c, "あなたは今クッキーを持っています。", [cookie])
    else
        the_cookie = cookies[1]
        write!(c, "あなたは正常に確認されました")
    end
end

export main
end
```
