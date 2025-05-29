```
dxdt!(du,u,p::uvwMeshArrays,tim)
```

グリッド化されたフィールド（3D; ハロー付き）から位置 `u` (`x,y,z,fIndex`) への速度を補間して、位置の時間微分 `du_dt` を計算します。

# 拡張ヘルプ

```jldoctest; output = false
using IndividualDisplacements
u,v,w,pos,func=vortex_flow_field(format=:MeshArray)
F=FlowFields(u,u,v,v,0*w,1*w,[0,3*pi],func)
I=Individuals(F,pos...)
∫!(I)

using CairoMakie
J=InDiPlot( data=(I=I,), options=(plot_type=:simple_plot2,) )
f=plot(J)

ref=[6.16, 7.23, 1.29, 1.0] # hide
prod(isapprox.(I.📌,ref,atol=1.0)) # hide

# output

true
```
