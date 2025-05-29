```
@computed mutable struct [...] end
```

フィールドを自動的に再計算します。

フィールドには `=` を使って式を割り当てることができ、その式の中の変数のいずれかが設定されると再評価されます。

# 例

```jldocs
julia> @computed mutable struct SinCos
    x::Float64
    thesincos::Tuple{Float64,Float64} = sincos(x)
end

julia> sc = SinCos(0.0)
SinCos(0.0, (0.0, 1.0))

julia> sc.x = pi/2
1.5707963267948966

julia> sc.thesincos
(1.0, 6.123233995736766e-17)
```
