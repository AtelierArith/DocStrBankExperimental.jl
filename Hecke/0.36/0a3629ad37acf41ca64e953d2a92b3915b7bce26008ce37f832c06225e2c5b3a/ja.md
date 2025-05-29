```
cyclotomic_field_as_cm_extension(n::Int; cached::Bool = true)
				                  -> RelSimpleNumField, RelSimpleNumFieldElem
```

整数 `n` を与えると、$E = \mathbb{Q}(\zeta_n)$ の `n` 番目の巡回体を、$\zeta_n + \zeta_n^{-1}$ によって生成される最大実部分体 `K` の二次拡張として返します。

# 例

```jldoctest
julia> E, b = cyclotomic_field_as_cm_extension(6)
(Relative number field of degree 2 over maximal real subfield of cyclotomic field of order 6, z_6)

julia> base_field(E)
Number field with defining polynomial $ - 1
  over rational field

```
