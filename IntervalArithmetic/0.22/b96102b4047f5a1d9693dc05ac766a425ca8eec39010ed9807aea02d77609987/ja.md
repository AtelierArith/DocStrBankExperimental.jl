```
isguaranteed(x::BareInterval)
isguaranteed(x::Interval)
isguaranteed(x::Complex{<:Interval})
```

区間がすべての可能な数値誤差を包含することが保証されていないかどうかをテストします。これは、`convert(::Type{<:Interval}, ::Real)`を使用して[`Interval`](@ref)が構築されるときに発生します。これは、区間と`Real`型を混合する際に暗黙的に発生する可能性があります。

`BareInterval`と`Number`の間の変換が禁止されているため、これは`isguaranteed(::BareInterval) == true`を意味します。

複素区間`x`の場合、これは`isguaranteed(real(x)) & isguaranteed(imag(x))`と意味的に同等です。

# 例

```jldoctest
julia> isguaranteed(bareinterval(1))
true

julia> isguaranteed(interval(1))
true

julia> isguaranteed(convert(Interval{Float64}, 1))
false

julia> isguaranteed(interval(1) + 0)
false
```
