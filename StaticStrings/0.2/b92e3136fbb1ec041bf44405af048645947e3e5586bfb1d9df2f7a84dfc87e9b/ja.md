```
padded"string[PAD]"N
```

`N` コードユニットの "string" から [`PaddedStaticString`](@ref) を作成します。提供された文字列の最後のコードユニットが `PAD` になります。

# 例

```jldoctest
julia> padded"私は元気です。 ありがとうございました。 "64
padded"私は元気です。 ありがとうございました。 "64

julia> padded"私は元気です。 ありがとうございました。 "64 |> StaticString
static"私は元気です。 ありがとうございました。      "64
```
