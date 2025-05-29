```
ConstValueShape{T} <: AbstractValueShape
```

`ConstValueShape`は、型`T`の定数値の形状を説明します。

コンストラクタ:

```
ConstValueShape(value)
```

`value`は任意の型である可能性があり、例えば定数スカラー値や配列などです:

```
ConstValueShape(4.2)
ConstValueShape([11 21; 12 22])
```

定数値の形状は自由度がゼロです（[`totalndof`](@ref）を参照）。

[`AbstractValueShape`](@ref)のドキュメントも参照してください。
