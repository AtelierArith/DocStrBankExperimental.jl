```
ElementConstraint{Teleobj,λinod,λfield,Nu,Treq,Tg,Tgargs,Tmode} <: AbstractElement
```

An element to apply optimisation equality/inequality constraints on the element-results of  another "target" element. The target element must *not* be added separately to the model.  Instead, the  `ElementType`, and the named arguments to the target element are provided as input to the  `ElementConstraint` constructor.

This element generates a time varying optimisation constraint. For example: find `A`-parameters so that    at all times, the element-result von-Mises stress does not exceed a given value. 

The Lagrangian multiplier introduced by this optimisation constraint is of class :U   

# Named arguments to the constructor

  * `λinod::𝕫`            The element-node number of the Lagrange multiplier.
  * `λfield::Symbol`      The field of the Lagrange multiplier.
  * `req`                 A request for element-results to be extracted from the target element, see [`@request`](@ref).                       The request is formulated as if adressed directly to the target element (no "prefixing" with                        `eleres`, see "Requestable internal variables")
  * `gₛ::𝕣=1.`             A scale for the gap.
  * `λₛ::𝕣=1.`             A scale for the Lagrange multiplier.
  * `gap`                 a gap function `gap(eleres,X,U,A,t,gargs...)→ℝ`                       `X` and `U` are tuples (derivates of dofs...), and `∂0(X)`,`∂1(X)`,`∂2(X)`                        must be used by `cost` to access the value and derivatives of `X` (resp. `U`).                       `X`, `U` and `A` are the degrees of freedom of the element `ElementType`.
  * `gargs::NTuple`       Additional inputs to the gap function.
  * `mode::Function`      where `mode(t::ℝ) -> Symbol`, with value `:equal`,                        `:positive` or `:off` at any time. An `:off` constraint                        will set the Lagrange multiplier to zero.
  * `ElementType`         The named of the constructor for the relevant element
  * `elementkwargs`       A named tuple containing the named arguments of the `ElementType` constructor.

# Requestable internal variables

From `ElementConstraint` one can request

  * `λ`                   The constraints Lagrange multiplier
  * `gap`                 The constraints gap function

From the target element on can request

  * `eleres(...)`         where `...` is the list of requestables from the target element.  It must be "prefixed" by                        `eleres` to prevent possible confusion with variables requestable from `ElementConstraint`.

δX

# Example

```
@once gap(eleres,X,U,A,t) = eleres.Fh^2
ele1 = addelement!(model,ElementCoonstraint,[nod1];req=@request(Fh),
                   gap,λinod=1,λfield=:λ,mode=equal, 
                   ElementType=AnchorLine,
                   elementkwargs=(Δxₘtop=[5.,0,0], xₘbot=[250.,0],L=290., buoyancy=-5e3))
```

See also: [`Hold`](@ref), [`DofConstraint`](@ref), [`off`](@ref), [`equal`](@ref), [`positive`](@ref), [`@request`](@ref)
