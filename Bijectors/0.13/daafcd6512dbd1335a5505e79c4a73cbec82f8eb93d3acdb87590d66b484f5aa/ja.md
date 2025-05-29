```
Coupling{F, M}(θ::F, mask::M)
```

[1] で定義されたカップリングレイヤーを実装します。

# 例

```jldoctest
julia> using Bijectors: Shift, Coupling, PartitionMask, coupling, couple

julia> m = PartitionMask(3, [1], [2]); # <= x[1] の変換をパラメータ化するために x[2] を使用します

julia> cl = Coupling(Shift, m); # <= `y[1:1] = x[1:1] + x[2:2]` を実行します;

julia> x = [1., 2., 3.];

julia> cl(x)
3-element Vector{Float64}:
 3.0
 2.0
 3.0

julia> inverse(cl)(cl(x))
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> coupling(cl) # `θ -> b(⋅, θ)` の `Bijector` マップを取得します
Shift

julia> couple(cl, x) # `x` から得られる `Bijector` を取得します
Shift([2.0])

julia> with_logabsdet_jacobian(cl, x)
([3.0, 2.0, 3.0], 0.0)
```

# 参考文献

[1] Kobyzev, I., Prince, S., & Brubaker, M. A., Normalizing flows: introduction and ideas, CoRR, (),  (2019). 
