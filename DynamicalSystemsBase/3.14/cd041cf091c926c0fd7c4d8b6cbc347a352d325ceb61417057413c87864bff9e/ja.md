```
set_parameters!(ds::DynamicalSystem, p = initial_parameters(ds))
```

[`current_parameters`](@ref)`(ds)`のパラメータ値を`p`の値に一致させます。これは、`p`のキーをループしてインプレースで上書きすることで行われるため、`p`はパラメータインデックスを値にマッピングする任意のコンテナ（`Vector{Real}`、`Vector{Pair}`、または`AbstractDict`など）であることができます。

`p`のキーは、[`set_parameter!`](@ref)に渡すことができる有効なキーでなければなりません。
