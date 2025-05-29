```
OrderedSet
```

`OrderedSet`は、エントリに特定の順序がある単純な集合です。この順序は挿入順序を指し、集合に対して決定論的な反復を可能にします。

注意: 特定の型のOrderedSetを作成するには、次のように型を指定する必要があります。

```julia
os = OrderedSet{Int}(3)
push!(os, [1,2]...)
```
