```julia
struct PartitionSpace{T<:Integer, P<:EqualitySampler.AbstractPartitionSpace}
```

```julia
# コンストラクタ
PartitionSpace(k::T, ::Type{U} = EqualitySampler.DistinctPartitionSpace)
```

パーティションの空間を表す型です。`EqualitySampler.AbstractPartitionSpace`は、パーティションが重複を含むべきか、または異なるべきかを示します。たとえば、異なるイテレータは`[1, 1, 2]`を返しますが、`[2, 2, 1]`や`[1, 1, 3]`は返しません。これらは`P = EqualitySampler.DuplicatedPartitionSpace`のときに返されます。
