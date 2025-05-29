```
scalartype(op::AbstractObservable)
```

演算子の基になるスカラー場の型を返します。これは、ベクトル値である可能性のある演算子の要素型を [`eltype`](@ref) で返すものとは異なる場合があります。

[`AbstractObservable`](@ref) インターフェースの一部です。

!!! note
    新しい型は、このメソッドを明示的に実装する必要はありません。実装は、[`AbstractObservable`](@ref) の型パラメータに基づいて提供されます。

