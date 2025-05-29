```
dxdt!(du,u,P::uvArrays,tim)
```

Interpolate velocity from gridded fields (2D; NO halos) to position `u` (`x,y`) to compute the derivative of position v time  `du_dt`.

# Extended help

```jldoctest; output = false
using IndividualDisplacements
u,v,w,pos=random_flow_field(format=:Array)
F=FlowFields(u,u,v,v,[0,1.0])
I=Individuals(F,pos...)
∫!(I)

isa(I.📌,Vector)

# output

true
```
