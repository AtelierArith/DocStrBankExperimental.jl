```
SmallBitSet{U<:Unsigned} <: AbstractSet{Int}

SmallBitSet{U}([iter])
SmallBitSet([iter])
```

`SmallBitSet{U}` は、`1` から `U` のビット長までの整数を保持できる不変集合です。引数なしで呼び出すと、空の集合が返されます。`U` が省略されると、`UInt` が取られます。

集合に対するすべての非変異関数がサポートされています。対応する `!` 関数の非変異アナログ [`push`](@ref push(::SmallBitSet, ::Vararg{Any})), [`pop`](@ref pop(::SmallBitSet)) および [`delete`](@ref) も提供されています。
