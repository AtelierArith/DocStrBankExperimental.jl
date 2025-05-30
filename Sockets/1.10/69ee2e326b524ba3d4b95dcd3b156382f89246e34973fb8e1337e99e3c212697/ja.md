```
getaddrinfo(host::AbstractString, IPAddr=IPv4) -> IPAddr
```

指定された `IPAddr` タイプの `host` の最初の IP アドレスを取得します。DNS ルックアップを行う可能性があるオペレーティングシステムの基盤となる getaddrinfo 実装を使用します。
