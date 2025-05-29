### Remote <: Toolips.ServerExtension

  * type::Vector{Symbol}
  * remotefunction::Dict{Int64, Function}
  * f::Function
  * logins::Dict{String, Hash}
  * users::Dict{Vector{UInt8}, String}
  * access::Dict{String, Int64}
  * motd::String - ログイン画面に表示されるメッセージ。

リモート拡張機能を使用すると、別のJulia REPLからサーバーに接続できます。最初の位置引数として代替のリモート関数を提供することができ、2番目の位置引数として新しいサービング関数を提供することもできます。リモート関数はConnectionとStringを受け取る必要があります。サービング関数はConnectionのみを受け取る必要があります。`remotefunction`は、レベルをキー、関数を値とする`Dict`です。次に、`usernames`ベクターにそのようなキーを設定します。このベクターはVector{Pair{String, Pair{String, Int64}}}です。以下のコンストラクタを参照して例を確認してください。`remotefunction`に提供される関数は、`RemoteConnection`または`Toolips.AbstractConnection`を受け取る必要があります。

##### 例

```
r = Remote()
st = ServerTemplate(extensions = [Remote()])
```

---

##### コンストラクタ

Remote(remotefunction::Function = Dict{Int64, Function}(1 => controller()), usernames::Vector{Pair{String, Pair{String, Int64}}} = ["root" => "1234" => 1];         motd::String, serving_f::Function)
