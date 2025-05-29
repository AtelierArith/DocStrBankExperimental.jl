```
@register_array_symbolic(expr, define_promotion = true)
```

例:

```julia
# 例えば、バンダーモンドはnベクトルを受け取り、n x n行列を返します
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

`define_promotion = true`の場合、次の形式の昇格メソッドが定義されます:

```julia
SymbolicUtils.promote_symtype(::typeof(f_registered), args...) = # 推論または注釈された戻り値の型
```

複数の登録オーバーロードを1つの関数に対して定義する場合、最初のものを除いて、他のすべての登録は`define_promotion`を`false`に設定する必要があります。メソッドの上書きを避けるためです。
