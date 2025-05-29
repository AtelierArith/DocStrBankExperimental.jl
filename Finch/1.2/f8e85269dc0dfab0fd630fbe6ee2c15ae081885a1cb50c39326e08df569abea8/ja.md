```
protocolize(tns, protos...)
```

次元 `n` に対してプロトコル `protos[n]` を使用して `ProtocolizedArray` を作成します。もし `protos[n]` が何もない場合は、何もしません。詳細については、[Iteration Protocols](@ref) のドキュメントを参照してください。例えば、行列 `A` の内側の次元に沿ってギャロップするには、`A[gallop(i), j]` と書き、これは `protocolize(A, gallop, nothing)[i, j]` になります。
