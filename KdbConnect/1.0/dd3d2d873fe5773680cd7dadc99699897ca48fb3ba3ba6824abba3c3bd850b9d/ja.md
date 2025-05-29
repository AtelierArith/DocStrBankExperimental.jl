```
open(conn::KdbConnectionInfo)::KdbHandle
```

KDBインスタンスへの接続を開きます。オープン接続への`KdbHandle`を返します。また、`do`構文もサポートしています：

```
open(conn::KdbConnectionInfo) do h
    execute(h,...)
end
```
