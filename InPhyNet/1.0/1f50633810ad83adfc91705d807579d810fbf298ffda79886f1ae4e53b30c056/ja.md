ネットワークのリストを返します。各エントリは、`subsets` に含まれる各サブセットで名前付けされた分類群のみを含むように剪定された `net` のコピーです。`subsets` は、ネストされたベクターの代わりに文字列の個別ベクターでも構いません（以下の例を参照）。

# 例

```julia
net = readnewick("((t1,t2),(t3,t4));")
prune_network(net, [["t1", "t2"], ["t3", "t4"]])
> 2-element Vector{HybridNetwork}: (t1, t2); and (t3, t4);

prune_network(net, ["t1", "t2", "t3"])
```
