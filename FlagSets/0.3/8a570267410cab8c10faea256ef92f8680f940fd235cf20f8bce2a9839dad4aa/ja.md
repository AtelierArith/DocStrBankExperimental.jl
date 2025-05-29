```
FlagSet{FlagType,BaseType<:Integer} <: AbstractSet{FlagType}
```

有限なオブジェクト（フラグ）の宇宙の部分集合である集合のスーパークラスであり、各集合は`BaseType`型の整数としてエンコードされます。フラグセットは`BitSet`と同様に実装されています。

もし`T <: FlagSet{B,F}`であれば、`typemax(T)`は`F`型のフラグの有限集合です。もし`set isa T`であれば、`set`は`typemax(T)`の部分集合です。

詳細については[`@flagset`](@ref)および[`@flagset_type`](@ref)を参照してください。
