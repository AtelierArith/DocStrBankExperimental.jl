```julia
respond!(c::AbstractConnection, args ...) -> ::Nothing
```

`Toolips`サーバーからのより詳細な応答である`respond!`は、HTTP応答にカスタムヘッダーを追加し、異なるコードで応答し、クッキーを設定することを可能にします。

```julia
# 基本メソッド（主に内部用）
respond!(c::AbstractConnection, resp::HTTP.Response, headers::Pair{String, String} ...)
# 通常のヘッダー/コードディスパッチ
respond!(c::AbstractConnection, body::String = "", headers::Pair{String, String} ...; code::Int64 = 200)
```

応答にクッキーを設定するための`Vector{Cookie}`ディスパッチ（`Cookie`および`get_cookies`を参照）：

```julia
respond!(c::AbstractConnection, body::String, cookies::Vector{Cookie}, headers::Pair{String, String} ...; 
    code::Int64 = 20)
```

メソッドリストの説明

  * 参照: `write!`, `get_target`, `Connection`, `route`, `start!`
