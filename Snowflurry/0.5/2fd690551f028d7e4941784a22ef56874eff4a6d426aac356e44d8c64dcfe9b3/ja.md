```
get_host(Client)
```

`Client`の`QPU`サービスへの接続のためのホストURLを返します。  

# 例

```jldoctest
julia> c = Client(
            host = "http://example.anyonsys.com",
            user = "test_user",
            access_token = "not_a_real_access_token"
        );

julia> get_host(c)
"http://example.anyonsys.com"

```
