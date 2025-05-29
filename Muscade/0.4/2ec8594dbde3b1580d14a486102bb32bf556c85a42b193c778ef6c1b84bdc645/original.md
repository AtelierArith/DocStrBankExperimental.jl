```
SingleUdof{XField,Ufield,Tcost} <: AbstractElement
```

An that creates a Udof, and associates a cost to its value. Thev alue of the Udof is applied as a load to a Xdof on the same node.  

# Named arguments to the constructor

  * `Xfield::Symbol`.
  * `Ufield::Symbol`.
  * `cost::Function`, where    `cost(x::ℝ,t::ℝ[,costargs...]) → ℝ` if `class` is `:X` or `:U`, and    `cost(x::ℝ,    [,costargs...]) → ℝ` if `class` is `:A`.
  * `costargs::NTuple`

# Requestable internal variables

  * `cost`, the value of the cost.

# Example

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,SingleUdofCost,[node];Xfield=:tx,Ufield=:utx,
                    costargs=(3.,),cost=(x,t,three)->(x/three)^2)
```

See also: [`DofCost`](@ref), [`ElementCost`](@ref)
