```
alphabet(
    X::PropositionalLogiset,
    sorted=true;
    test_operators::Union{Nothing,AbstractVector{<:TestOperator},Base.Callable}=nothing,
    discretizedomain=false,
    y::Union{Nothing, AbstractVector}=nothing,
)::MultivariateScalarAlphabet
```

Constructs an alphabet based on the provided `PropositionalLogiset` `X`, with optional parameters:

  * `sorted`: whether to sort the atoms in the sub-alphabets (i.e., the threshold domains),   by a truer-first policy (default: true)
  * `test_operators`: test operators to use (defaulted to `[≤, ≥]` for real-valued features, and `[(==), (≠)]` for other features, e.g., categorical)
  * `discretizedomain`: whether to discretize the domain (default: false)
  * `y`: vector used for discretization (required if `discretizedomain` is true)

Returns a `UnionAlphabet` containing `ScalarCondition` and `UnivariateScalarAlphabet`.
