```
atom_name(species)
atom_name(sys::AbstractSystem, i)
```

`species`の原子名（`Symbol`）または`sys`の名前のベクトルを返します。

`name`フィールドがゼロまたは定義されていない場合は、デフォルトで[`atomic_symbol`](@ref)になります。
