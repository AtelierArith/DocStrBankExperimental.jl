```julia
mount(fpair::Pair{String, String}) -> ::Route{Connection}/::Vector{Route{Connection}}
```

`mount`は、ファイルまたはディレクトリ内のすべてのファイルを提供するルートを作成します。 `fpair`の最初の部分はターゲットルートパスであり、例えば`/`はホームを示します。 提供されたパスがディレクトリである場合、関数は`Vector{AbstractRoute}`を返します。 単一のファイルの場合、これはルートになります。

```example
module MyServer
using Toolips

logger = Toolips.Logger()

filemount::Route{Connection} = mount("/" => "templates/home.html")

dirmount::Vector{<:AbstractRoute} = mount("/files" => "public")

export filemount, dirmount, logger
end
```
