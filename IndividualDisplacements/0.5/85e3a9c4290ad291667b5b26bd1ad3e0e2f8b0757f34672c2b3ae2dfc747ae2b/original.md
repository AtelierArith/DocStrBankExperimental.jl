```
dxdt!(du,u,p::uvMeshArrays,tim)
```

Interpolate velocity from gridded fields (2D; with halos) to position `u` (`x,y,fIndex`) to compute the derivative of position v time  `du_dt`.

# Extended help

```jldoctest; output = false
using IndividualDisplacements
u,v,w,pos,func=random_flow_field(format=:MeshArray)
F=FlowFields(u,u,v,v,[0,1.0],func)
I=Individuals(F,pos...)
∫!(I)

isa(I.📌,Vector)

# output

true
```
