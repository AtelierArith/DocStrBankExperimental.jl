```
huge
```

`huge` は、不要な型昇格なしでさまざまな計算に使用できる（わお！）巨大な数を表します。

`huge` は次のように定義されています：

  * `1.0f+6` は `Float32` の場合
  * `1e+12` は `Float64` の場合
  * `big"1e+24"` は `BigFloat` の場合
  * `inv(tiny(F))` は任意の型 `F <: AbstractFloat` の場合

# 例

```jldoctest
julia> huge
huge

julia> 1 + huge
1.000000000001e12

julia> huge + 1
1.000000000001e12

julia> 1f0 + huge
1.000001f6

julia> big"1.0" + huge
1.000000000000000000000001e+24

julia> big"1" + huge
1.000000000000000000000001e+24
```

参照： [`tiny`](@ref)
