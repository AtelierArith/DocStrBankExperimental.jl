```
GenericNonlinearExpr{V}(head::Symbol, args::Vector{Any})
GenericNonlinearExpr{V}(head::Symbol, args::Any...)
```

The scalar-valued nonlinear function `head(args...)`, represented as a symbolic expression tree, with the call operator `head` and ordered arguments in `args`.

`V` is the type of [`AbstractVariableRef`](@ref) present in the expression, and is used to help dispatch JuMP extensions.

## `head`

The `head::Symbol` must be an operator supported by the model.

The default list of supported univariate operators is given by:

  * [`MOI.Nonlinear.DEFAULT_UNIVARIATE_OPERATORS`](@ref)

and the default list of supported multivariate operators is given by:

  * [`MOI.Nonlinear.DEFAULT_MULTIVARIATE_OPERATORS`](@ref)

Additional operators can be add using [`@operator`](@ref).

See the full list of operators supported by a [`MOI.ModelLike`](@ref) by querying the [`MOI.ListOfSupportedNonlinearOperators`](@ref) attribute.

## `args`

The vector `args` contains the arguments to the nonlinear function. If the operator is univariate, it must contain one element. Otherwise, it may contain multiple elements.

Given a subtype of [`AbstractVariableRef`](@ref), `V`, for `GenericNonlinearExpr{V}`, each element must be one of the following:

  * A constant value of type `<:Real`
  * A `V`
  * A [`GenericAffExpr{T,V}`](@ref)
  * A [`GenericQuadExpr{T,V}`](@ref)
  * A [`GenericNonlinearExpr{V}`](@ref)

where `T<:Real` and `T == value_type(V)`.

## Unsupported operators

If the optimizer does not support `head`, an [`MOI.UnsupportedNonlinearOperator`](@ref) error will be thrown.

There is no guarantee about when this error will be thrown; it may be thrown when the function is first added to the model, or it may be thrown when [`optimize!`](@ref) is called.

## Example

To represent the function $f(x) = sin(x)^2$, do:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f = sin(x)^2
sin(x) ^ 2.0

julia> f = GenericNonlinearExpr{VariableRef}(
           :^,
           GenericNonlinearExpr{VariableRef}(:sin, x),
           2.0,
       )
sin(x) ^ 2.0
```
