```
static"string"[N]
```

"string"から[`StaticString`](@ref)を作成します。オプションで、コードユニットの数`N`を指定します。

# 例

```jldoctest
julia> static"großartig"
static"großartig"10

julia> static"verehrungswürdig"20
static"verehrungswürdig\0\0\0"20
```
