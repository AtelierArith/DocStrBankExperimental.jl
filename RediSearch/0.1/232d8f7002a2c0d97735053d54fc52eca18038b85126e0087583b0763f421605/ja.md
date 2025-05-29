```
Client(index_name::AbstractString; kwargs....) -> Jedis.Client
```

RediSearchクライアントを設定します。クライアントにはインデックス名とJedisクライアント構造体が含まれます。Kwargsは任意のJedisクライアントのkwargsとして含まれます。

# フィールド

  * `index_name::String`: クライアントで作成されるインデックス名。
  * `client::Jedis.Client`: Jedisパッケージを通じて作成されたクライアントオブジェクト。

# 例

```julia-repl
julia> client = Client("myIdx");

julia> client = Client("myIdx"; host="localhost", port=6379);
```
