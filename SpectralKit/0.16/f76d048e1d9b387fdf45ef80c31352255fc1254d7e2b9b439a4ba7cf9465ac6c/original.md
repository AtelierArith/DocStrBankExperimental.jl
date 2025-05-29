`is_function_basis(::Type{F})`

`is_function_basis(f::F)`

Test if the argument (value or type) is a *function basis*, supporting the following interface:

  * [`domain`](@ref) for querying the domain,
  * [`dimension`](@ref) for the dimension,
  * [`basis_at`](@ref) for function evaluation,
  * [`grid`](@ref) to obtain collocation points.
  * `length` and `getindex` for multivariate bases `(domain_kind(domain(basis)) == :multivariate)`, getindex returns a compatible marginal basis

[`linear_combination`](@ref) and [`collocation_matrix`](@ref) are also supported, building on the above.

Can be used on both types (preferred) and values (for convenience).
