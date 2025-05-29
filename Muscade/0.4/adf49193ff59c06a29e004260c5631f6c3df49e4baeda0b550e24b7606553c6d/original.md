```
DofCost{Class,Nx,Nu,Na,xinod,xfield,uinod,ufield,ainod,
    afield,Tcost,Tcostargs} <: AbstractElement
```

An element to apply costs on combinations of dofs.  

# Named arguments to the constructor

  * `xinod::NTuple{Nx,𝕫}=()`       For each X-dof to enter `cost`, its element-node number.
  * `xfield::NTuple{Nx,Symbol}=()` For each X-dof to enter `cost`, its field.
  * `uinod::NTuple{Nu,𝕫}=()`       For each U-dof to enter `cost`, its element-node number.
  * `ufield::NTuple{Nu,Symbol}=()` For each U-dof to enter `cost`, its field.
  * `ainod::NTuple{Na,𝕫}=()`       For each A-dof to enter `cost`, its element-node number.
  * `afield::NTuple{Na,Symbol}=()` For each A-dof to enter `cost`, its field.
  * `class:Symbol`                 `:A` for cost on A-dofs only, `:I` ("instant") otherwise.
  * `cost::Function`               if `class==:I`, `cost(X,U,A,t,costargs...)→ℝ`                                if `class==:A`, `cost(A,costargs...)→ℝ`                                 `X` and `U` are tuples (derivates of dofs...), and `∂0(X)`,`∂1(X)`,`∂2(X)`                                 must be used by `cost` to access the value and derivatives of `X` (resp. `U`)
  * `costargs::NTuple`

# Requestable internal variables

  * `cost`, the value of the cost.

# Example

```
ele1 = addelement!(model,DofCost,[nod1],xinod=(1,),field=(:tx1,),
       class=:I,cost=(X,U,A,t)->X[1]^2
```

See also: [`SingleDofCost`](@ref), [`ElementCost`](@ref), [`addelement!`](@ref)  
