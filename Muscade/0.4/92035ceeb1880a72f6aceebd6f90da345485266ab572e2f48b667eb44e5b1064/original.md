```
DofLoad{Tvalue,Field} <: AbstractElement
```

An element to apply a loading term to a single X-dof.  

# Named arguments to the constructor

  * `field::Symbol`.
  * `value::Function`, where `value(t::ℝ) → ℝ`.

# Requestable internal variables

  * `F`, the value of the load.

# Examples

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,DofLoad,[node];field=:tx,value=t->3t-1)
```

See also: [`Hold`](@ref), [`DofCost`](@ref)  
