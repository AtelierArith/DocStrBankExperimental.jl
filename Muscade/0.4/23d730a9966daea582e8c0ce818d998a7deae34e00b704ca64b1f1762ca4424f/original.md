```
DofConstraint{λclass,Nx,Nu,Na,xinod,xfield,uinod,ufield,ainod,
    afield,λinod,λfield,Tg,Tmode} <: AbstractElement
```

An element to apply physical/optimisation equality/inequality constraints on dofs. 

The constraints are holonomic, i.e. they apply to the values, not the time derivatives, of the involved dofs.  This element is very general but not very user-friendly to construct, factory functions are provided for better useability.  The sign convention is that the gap `g≥0` and the Lagrange multiplier `λ≥0`.

This element can generate three classes of constraints, depending on the input argument `λclass`.

  * `λclass=:X` Physical constraint.  In mechanics, the Lagrange multiplier dof is a   generalized force, dual of the gap. The gap function must be of the form `gap(x,t,gargs...)`.
  * `λclass=:U` Time varying optimisation constraint. For example: find `A`-parameters so that  at all times, the response does not exceed a given criteria. The gap function must be of the form     `gap(x,u,a,t,gargs...)`.
  * `λclass=:A` Time invariant optimisation constraint. For example: find `A`-parameters such that  `A[1]+A[2]=gargs.somevalue`. The gap function must be of the form `gap(a,gargs...)`.

# Named arguments to the constructor

  * `xinod::NTuple{Nx,𝕫}=()`       For each X-dof to be constrained, its element-node number.
  * `xfield::NTuple{Nx,Symbol}=()` For each X-dof to be constrained, its field.
  * `uinod::NTuple{Nu,𝕫}=()`       For each U-dof to be constrained, its element-node number.
  * `ufield::NTuple{Nu,Symbol}=()` For each U-dof to be constrained, its field.
  * `ainod::NTuple{Na,𝕫}=()`       For each A-dof to be constrained, its element-node number.
  * `afield::NTuple{Na,Symbol}=()` For each A-dof to be constrained, its field.
  * `λinod::𝕫`                     The element-node number of the Lagrange multiplier.
  * `λclass::Symbol`               The class (`:X`,`:U` or `:A`) of the Lagrange multiplier.                                 See the explanation above for classes of constraints
  * `λfield::Symbol`               The field of the Lagrange multiplier.
  * `gap::Function`                The gap function.
  * `gargs::NTuple`                Additional inputs to the gap function.
  * `mode::Function`               where `mode(t::ℝ) -> Symbol`, with value `:equal`,                                 `:positive` or `:off` at any time. An `:off` constraint                                 will set the Lagrange multiplier to zero.

# Example

```jldoctest; output = false
using Muscade
model           = Model(:TestModel)
n1              = addnode!(model,𝕣[0]) 
e1              = addelement!(model,DofConstraint,[n1],xinod=(1,),xfield=(:t1,),
                              λinod=1, λclass=:X, λfield=:λ1,gap=(x,t)->x[1]+.1,
                              mode=positive)
e2              = addelement!(model,QuickFix  ,[n1],inod=(1,),field=(:t1,),
                              res=(x,u,a,t)->0.4x.+.08+.5x.^2)
initialstate    = initialize!(model)
setdof!(initialstate,1.;field=:λ1)
state           = solve(SweepX{0};initialstate,time=[0.],verbose=false) 
X               = state[1].X[1]

# output

2-element Vector{Float64}:
 -0.09999152289496528
  0.04500254313151041
```

See also: [`Hold`](@ref), [`ElementConstraint`](@ref), [`off`](@ref), [`equal`](@ref), [`positive`](@ref)
