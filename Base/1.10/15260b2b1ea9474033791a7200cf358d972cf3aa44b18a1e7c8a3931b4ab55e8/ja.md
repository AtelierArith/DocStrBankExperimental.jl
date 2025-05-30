```
@big_str str
```

文字列を[`BigInt`](@ref)または[`BigFloat`](@ref)に解析し、文字列が有効な数値でない場合は`ArgumentError`をスローします。整数の場合、`_`は文字列内で区切り文字として許可されています。

# 例

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: invalid number format _ for BigInt or BigFloat
[...]
```
