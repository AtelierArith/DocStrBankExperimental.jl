```
components(A::GridArray{T})
```

`A`を`T`の各コンポーネントに対して1つずつの`GridArray`のタプルに分割します。

コンポーネントのデータは元の配列と共有されていることに注意してください。

例えば、`A isa GridArray{SVector{3, Float64}}`の場合、`NTuple{3, GridArray{Float64}}`型のタプルが返されます。
