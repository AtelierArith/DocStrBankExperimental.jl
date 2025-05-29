```
dxdt!(du,u,P::uvwArrays,tim)
```

Interpolate velocity from gridded fields (3D; NO halos) to position `u` (`x,y,z`) to compute the derivative of position v time  `du_dt`.

# Extended help

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
