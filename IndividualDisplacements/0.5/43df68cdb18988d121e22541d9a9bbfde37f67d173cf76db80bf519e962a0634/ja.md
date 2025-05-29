```
dxy_dt_replay(du,u,p::DataFrame,t)
```

MITgcm float_trajectories の出力から速度を補間し、位置の増分 `du` を返します。

# 拡張ヘルプ

```jldoctest; output = false
using IndividualDisplacements
p=dirname(pathof(IndividualDisplacements))
include(joinpath(p,"../examples/more/detailed_look.jl"))
prod(isapprox.(sol[:,end],ref[:,end],atol=1.0))

# output

true
```
