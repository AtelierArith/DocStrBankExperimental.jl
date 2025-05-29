```
create_quantum_env(client::Client)
```

QuEST環境作成関数を使用して新しい量子環境を作成します。

# 引数

  * `client::Client`: 量子環境が作成されるクライアント。

# 戻り値

  * 新しい量子環境。

# 例

```julia
client = Client()
env = create_quantum_env(client)
```
