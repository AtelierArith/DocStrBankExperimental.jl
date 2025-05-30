```
writesubtree!(IO, node, edge, dendroscope::Bool, namelabel::Bool,
              round_branch_lengths::Bool, digits::Integer, internallabel::Bool)
```

`node`を根とし、`edge`が`node`の親であると仮定して、サブネットワークの拡張ニューイック形式を書きます。

親の`edge`が`nothing`の場合、エッジ属性`ischild1`が使用され、`node`を根とするサブツリーを書くために正しいと仮定されます。これは、非根ノードから始まるサブツリーを書くのに便利です。例：

```julia
net = readnewick("(((A,(B)#H1:::0.9),(C,#H1:::0.1)),D);")
directedges!(net)
s = IOBuffer()
writesubtree!(s, net.node[7], nothing, false, true)
String(take!(s))
```

[`writenewick`](@ref)によって使用されます。
