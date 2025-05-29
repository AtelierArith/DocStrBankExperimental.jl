```
add_field_vec!(
    dest, 
    FieldData::Type{<:AbstractData}, 
    data_dims::Tuple{Vararg{NamedDimension}}, 
    Space::Type{<:AbstractSpace}, 
    a, 
    cellrange,
    src, 
    soff
) -> num_added::Int
```

`dest += a*src` を実装します。ここで `dest` は Field.values、`src` は Array、`a` は数値であり、`cellrange` で定義された領域に対して、`src` のインデックス `soff` から始まります。

使用された `src` の要素数を返します。

[`copytofield!`](@ref) と [`copyfieldto!`](@ref) の関係については、Array `src` と Field values `dest` を参照してください。
