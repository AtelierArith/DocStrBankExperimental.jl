```
QuickFix <: AbstractElement
```

An element for creating simple elements with "one line" of code.   Elements thus created have several limitations:

  * physical elements with only X-dofs.
  * only `R` can be espied.

The element is intended for testing.  Muscade-based applications should not include this in their API. 

# Named arguments to the constructor

  * `inod::NTuple{Nx,𝕫}`. The element-node numbers of the X-dofs.
  * `field::NTuple{Nx,Symbol}`. The fields of the X-dofs.
  * `res::Function`, where `res(X::ℝ1,X′::ℝ1,X″::ℝ1,t::ℝ) → ℝ1`, the residual.

# Examples

A one-dimensional linear elastic spring with stiffness 2.

```jldoctest; output = false
using Muscade
model = Model(:TestModel)
node1  = addnode!(model,𝕣[0])
node2  = addnode!(model,𝕣[1])
e = addelement!(model,QuickFix,[node1,node2];inod=(1,2),field=(:tx1,:tx1),
                res=(X,X′,X″,t)->Svector{2}(2*(X[1]-X[2]),2*(X[2]-X[1])) )

# output

Muscade.EleID(1, 1)                       
```
