```
prevpow(a, x)
```

`x`以下の最大の`a^n`、ここで`n`は非負整数です。`a`は1より大きく、`x`は1未満であってはなりません。

関連情報としては[`nextpow`](@ref)、[`isqrt`](@ref)があります。

# 例

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
