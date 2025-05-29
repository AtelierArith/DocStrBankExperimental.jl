```
I = LogicalIndices(io::CSeis)
```

`CartesianIndices`に似た構造を返し、CloudSeisデータコンテキストの論理的な開始位置とデルタによってオフセットされた線形インデックスから直交インデックスへの変換を可能にします。さらに、`LogicalIndices`はデータセット内のすべてのフレームをループ処理するための反復を実装しています。例えば、

```julia
io = csopen(AzContainer("foo"; storageaccount="bar))
idx = LogicalIndices(io)[2] # データセット内の2番目のフレームに対応するインデックスを取得します。
for idx in LogicalIndices(io)
    @show idx
    trcs, hdrs = getframe(io, idx)
end
```
