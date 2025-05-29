```
getproperty_direct(s::T, p::Symbol)
```

プライベートフィールドを持つ型のためのフォールバック `getproperty` 実装で、これは [`@private_struct`](@ref) によって示されます。

デフォルトでは、`getproperty_direct` は `getfield` をラップします。型に特別なプロパティが必要でありながら、プライベートフィールドを含む型にしたい場合は、`getproperty_direct` を実装できます。`T` のプライベートフィールドと一致しないプロパティ名については、このメソッドが使用されます。

`@private_method` タグが付けられたメソッド内にいる場合、プライベートアクセスを持つと注釈された引数は、`getproperty_direct` を直接呼び出します。これは、`getproperty_direct` がプライベートフィールドに直接アクセスすることもサポートする必要があることを意味します。
