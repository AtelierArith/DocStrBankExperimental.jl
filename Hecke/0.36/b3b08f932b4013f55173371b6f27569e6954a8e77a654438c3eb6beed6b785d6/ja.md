```
disc_log(b::T, x::T) where {T <: FinFieldElem}
```

整数 `s` を返します。これは $b^s = x$ となります。もしそのような `x` が存在しない場合、例外がスローされます。

# 例

```jldoctest
julia> F = GF(3,4); a = gen(F)^21;

julia> disc_log(gen(F), a)
21
```
