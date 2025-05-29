```
ElementCost{Teleobj,Treq,Tcost,Tcostargs} <: AbstractElement
```

An element to apply costs on another "target" element's dofs and element-results.   The target element must *not* be added separately to the model.  Instead, the  `ElementType`, and the named arguments to the target element are provided as input to the `ElementCost` constructor.

# Named arguments to the constructor

  * `req`                 A request for element-results to be extracted from the target element, see [`@request`](@ref).                       The request is formulated as if adressed directly to the target element (no "prefixing" with                        `eleres`, see "Requestable internal variables")
  * `cost`                a cost function `cost(eleres,X,U,A,t,costargs...)→ℝ`                       `X` and `U` are tuples (derivates of dofs...), and `∂0(X)`,`∂1(X)`,`∂2(X)`                        must be used by `cost` to access the value and derivatives of `X` (resp. `U`).                       `X`, `U` and `A` are the degrees of freedom of the element `ElementType`.
  * `costargs=(;)`        A named tuple of additional arguments to the cost function
  * `ElementType`         The named of the constructor for the relevant element
  * `elementkwargs`       A named tuple containing the named arguments of the `ElementType` constructor.

# Requestable internal variables

From `ElementConstraint` one can request

  * `cost`               The value of the cost

From the target element once can request

  * `eleres(...)`        where `...` is the list of requestables from the target element.  It must be "prefixed" by                       `eleres` to prevent possible confusion with variables requestable from `ElementConstraint`.

# Example

```
@once cost(eleres,X,U,A,t) = eleres.Fh^2
ele1 = addelement!(model,ElementCost,[nod1];req=@request(Fh),
                   cost=cost,ElementType=AnchorLine,
                   elementkwargs=(Λₘtop=[5.,0,0], xₘbot=[250.,0], L=290., buoyancy=-5e3))
```

See also: [`SingleDofCost`](@ref), [`DofCost`](@ref), [`@request`](@ref) 
