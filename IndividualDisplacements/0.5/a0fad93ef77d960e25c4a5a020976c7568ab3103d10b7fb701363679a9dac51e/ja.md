```
dxdt!(du,u,P::uvwArrays,tim)
```

グリッド化されたフィールド（3D; ハローなし）から位置 `u` (`x,y,z`) に対して速度を補間し、位置の時間微分 `du_dt` を計算します。

# 拡張ヘルプ

```jldoctest; output = false
using IndividualDisplacements
u,v,w,pos=vortex_flow_field(format=:Array)
F=FlowFields(u,u,v,v,0*w,1*w,[0,3*pi])
I=Individuals(F,pos...)
∫!(I)

ref=[9.35, 7.93, 1.28] # hide
prod(isapprox.(I.📌,ref,atol=1.0)) # hide

# output

true
```
