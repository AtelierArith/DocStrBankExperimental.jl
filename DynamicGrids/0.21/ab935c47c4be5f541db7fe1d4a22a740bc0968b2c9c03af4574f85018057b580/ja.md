```
Grid <: ParameterSource

Grid{K}()
Grid(K::Symbol)
```

キー `K` を持つグリッドをパラメータソースとして使用します。

ルールで実装されているのは次の通りです：

```julia
get(data, rule.myparam, I)
```

そして、ルールの構築時に次のように指定されます：

```julia
SomeRule(; myparam=Grid(:somegrid))
```
