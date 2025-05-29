```
from_dict(::Type{T}, d::AbstractDict{String}; kw...) where T
```

辞書 `d` をオプション型 `T` に変換します。この辞書 `d` の有効なフィールドの値は、キーワード引数によって上書きすることができます。

!!! compat "Configurations 0.17"
    `convert_to_option` インターフェースは変換のために非推奨です。代わりに、3引数または4引数の `from_dict` をオーバーロードしてください。詳細は [Type Conversion](@ref type-conversion) セクションを参照してください。


# 例

```julia-repl
julia> @option struct OptionA
           name::String = "Sam"
           age::Int = 25
       end

julia> d = Dict{String, Any}(
           "name" => "Roger",
           "age" => 10,
       );

julia> from_dict(OptionA, d; age=25)
OptionA(;
    name = "Roger",
    age = 25,
)
```
