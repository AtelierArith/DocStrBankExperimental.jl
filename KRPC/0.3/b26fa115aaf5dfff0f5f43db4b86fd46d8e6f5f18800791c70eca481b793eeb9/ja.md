```
kerbal_connect(client_name::String, host::String="localhost", port::Int64=50000, stream_port::Int64=50001)
```

`host`のポート`port`（ストリームポート`stream_port`を使用）に接続し、表示名`client_name`を使用します。デフォルトのローカルホスト構成のためにデフォルト値が設定されています。

# 例

ローカルホストに「test」として接続し、デフォルトポートを使用します：

```julia-repl
julia> conn = kerbal_connect("test")
```

ポート9001/9002を使用してローカルホストに接続します：

```julia-repl
julia> conn = kerbal_connect("test", "localhost", 9001, 9002)
```

IPアドレス192.168.1.1のサーバーに接続し、ポート9001/9002を使用します：

```julia-repl
julia> conn = kerbal_connect("test", "192.168.1.1", 9001, 9002)
```
