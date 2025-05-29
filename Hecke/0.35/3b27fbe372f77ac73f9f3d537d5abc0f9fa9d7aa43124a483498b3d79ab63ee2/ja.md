```
embedding(p::InfPlc) -> NumFieldEmb
```

実数の無限位を与えると、この位を定義する唯一の実埋め込みを返します。無限位が実数でない場合、エラーがスローされます。

参照: [`embeddings`](@ref)。

# 例

```jldoctest
julia> K, a = quadratic_field(5);

julia> embedding(real_places(K)[1])
Complex embedding corresponding to -2.24
  of real quadratic field defined by x^2 - 5
```
