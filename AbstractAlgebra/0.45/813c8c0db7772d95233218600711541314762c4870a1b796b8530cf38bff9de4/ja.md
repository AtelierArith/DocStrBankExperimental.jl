```
is_noetherian(R::Ring)
```

リング $R$ がノーザリアンであるかどうかを確認します。

# 例

```jldoctest
julia> R, x = polynomial_ring(ZZ, [:x]);

julia> is_noetherian(R)
true
```
