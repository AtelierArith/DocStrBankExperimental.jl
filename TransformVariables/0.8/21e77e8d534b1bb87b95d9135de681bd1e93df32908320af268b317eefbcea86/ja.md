```julia
inverse!(x, transformation, y)

```

`inverse(t, y)`を事前に確保されたベクトル`x`に入れ、`x`を返します。

`x`に対して一般化されたインデクシングが想定されます。

`x`の型を決定するには[`inverse_eltype`](@ref)を参照してください。
