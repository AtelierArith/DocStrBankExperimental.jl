```
tiny
```

`tiny` は、不要な型昇格なしでさまざまな計算に使用できる（わお！）小さな数を表します。

`tiny` は次のように定義されています：

  * `Float32` の場合は `1.0f-6`
  * `Float64` の場合は `1e-12`
  * `BigFloat` の場合は `big"1e-24"`
  * 任意の型 `F <: AbstractFloat` の場合は `10 * eps(F)`

# 例

```jldoctest
julia> tiny
tiny

julia> 1 + tiny
1.000000000001

julia> tiny + 1
1.000000000001

julia> 1f0 + tiny
1.000001f0

julia> big"1.0" + tiny
1.000000000000000000000001

julia> big"1" + tiny
1.000000000000000000000001
```

参照： [`huge`](@ref)
