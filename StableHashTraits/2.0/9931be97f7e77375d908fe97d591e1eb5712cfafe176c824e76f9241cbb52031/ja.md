```
omit_fields(x, fields::Symbol...)
omit_fields(x, fields::NTuple{<:Any, Symbol})
omit_fields(fields::Symbol...)
omit_fields(fields::NTuple{<:Any, Symbol})
```

`x`から`fields`を除外したオブジェクトを返します。これは`getfield`に従います。指定されたフィールドを選択するための関数を返すカリー化されたバージョンも存在します。

この関数は、フィールドの名前付きタプルを返すこと（例：`x -> (;x.a, x.b)`）とは異なり、返されるフィールドの型を狭めません。`x`の型`Any`のフィールドは、返される値の型`Any`のフィールドです。これにより、`pick*fields`が[`Transformer`](@ref)の`hoist*type`と安全に使用できることが保証されます。
