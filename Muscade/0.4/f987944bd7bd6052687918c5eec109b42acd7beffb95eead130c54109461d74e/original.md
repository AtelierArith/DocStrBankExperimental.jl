```
SingleDofCost{Derivative,Class,Field,Tcost} <: AbstractElement
```

An element with a single node, for adding a cost to a given dof.  

# Named arguments to the constructor

  * `class::Symbol`, either `:X`, `:U` or `:A`.
  * `field::Symbol`.
  * `cost::Function`, where 

      * `cost(x::ℝ,t::ℝ[,costargs...]) → ℝ` if `class` is `:X` or `:U`, and
      * `cost(x::ℝ,    [,costargs...]) → ℝ` if `class` is `:A`.
  * `costargs::NTuple=()`
  * `derivative::Int=0` 0, 1 or 2 - which time derivative of the dof enters the cost.

# Requestable internal variables

  * `cost`, the value of the cost.

# Example

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,SingleDofCost,[node];class=:X,field=:tx,
                    costargs=(3.,),cost=(x,t,three)->(x/three)^2)
```

See also: [`DofCost`](@ref), [`ElementCost`](@ref)
