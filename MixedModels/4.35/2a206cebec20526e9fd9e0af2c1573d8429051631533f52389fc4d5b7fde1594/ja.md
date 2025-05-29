```
ranef(m::LinearMixedModel; uscale=false)
```

モデル `m` のランダム効果の条件付きモードを `Vector{Matrix{T}}` として返します。

`uscale` が `true` の場合、ランダム効果は球面（すなわち `u`）スケールで、そうでない場合は元のスケールで返されます。

名前付きのバリアントについては、[`raneftables`](@ref) を参照してください。
