```
Complement{N, S<:LazySet{N}} <: LazySet{N}
```

集合の補集合を表す型、すなわち集合

$$
Y = \{y ∈ ℝ^n : y ∉ X\}.
$$

補集合はしばしば $C$ 上付き文字で表され、$Y = X^C$ のように書かれます。

### フィールド

  * `X` – 集合

### 注意事項

`X` が空であるか、全体集合、または半空間である場合、その補集合は凸です。

`X` は閉じていると仮定されているため、`X` が空であるか全体集合でない限り、その補集合は開いています（すなわち、閉じていません）。このライブラリでは、すべての集合は閉じているため、集合は通常境界で正確には表現されません。

補集合の補集合は元の集合に戻ります。

### 例

```jldoctest
julia> B = BallInf(zeros(2), 1.);

julia> C = Complement(B)
Complement{Float64, BallInf{Float64, Vector{Float64}}}(BallInf{Float64, Vector{Float64}}([0.0, 0.0], 1.0))

julia> Complement(C)
BallInf{Float64, Vector{Float64}}([0.0, 0.0], 1.0)
```
