```
@register_array_symbolic(expr)
```

例:

```julia
# 例えば、vandermondeはnベクトルを受け取り、n x n行列を返します
@register_array_symbolic vandermonde(x::AbstractVector) begin
    size=(length(x), length(x))
    eltype=eltype(x) # オプション、xの昇格されたeltypeがデフォルトになります
end
```

呼び出し可能な構造体に対しても登録できます:

```julia
@register_array_symbolic (c::Conv)(x::AbstractMatrix) begin
    size=size(x) .- size(c.kernel) .+ 1
    eltype=promote_type(eltype(x), eltype(c))
end
```
