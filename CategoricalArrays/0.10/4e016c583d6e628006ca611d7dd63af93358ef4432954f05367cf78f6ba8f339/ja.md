```
CategoricalValue{T <: Union{AbstractChar, AbstractString, Number}, R <: Integer}
```

`CategoricalPool`のレベルに対応する型`T`の値をラップするためのラッパーです。

`CategoricalValue`オブジェクトは、`==`および`isequal`によってラップされている型`T`の値と等しいと見なされます。ただし、`<`や`isless`のような順序比較は、値のプールに対して[`isordered`](@ref)が`true`である場合にのみ可能であり、その場合、プールの[`levels`](@ref DataAPI.levels)の順序が型`T`の値の標準的な順序ではなく使用されます。
