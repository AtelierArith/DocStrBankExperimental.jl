```
Hold <: AbstractElement
```

An element to set a single X-dof to zero.  

# Named arguments to the constructor

  * `field::Symbol`. The field of the X-dof to constraint.
  * `λfield::Symbol=Symbol(:λ,field)`. The field of the Lagrange multiplier.

# Example

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,Hold,[node];field=:tx)
```

See also: [`DofConstraint`](@ref), [`DofLoad`](@ref), [`DofCost`](@ref) 
