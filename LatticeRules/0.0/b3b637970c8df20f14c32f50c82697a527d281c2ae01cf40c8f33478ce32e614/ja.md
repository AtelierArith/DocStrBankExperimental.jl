```
LatticeRule32(s)
```

`s` 次元のランク-1 ラティスルールを返し、順序-2 の重みを持つデフォルトの生成ベクトルを使用します。

# 例

```jldoctest; setup = :(using LatticeRules)
julia> lattice_rule = LatticeRule32(16)
LatticeRule32{16}

julia> getpoint(lattice_rule, 123)
16-element Array{Float64,1}:
 0.8671875
 0.5390625
 0.6015625
 0.3671875
 0.6796875
 0.8203125
 0.3046875
 0.8515625
 0.7109375
 0.6328125
 0.5703125
 0.2578125
 0.6953125
 0.0390625
 0.2421875
 0.4453125

```

参照: [`getpoint`](@ref), [`ShiftedLatticeRule32`](@ref)
