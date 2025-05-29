```
build_parameter(
    _error::Function, domain::InfiniteScalarDomain;
    [num_supports::Int = 0,
    supports::Union{Real, Vector{<:Real}} = Float64[],
    sig_digits::Int = DefaultSigDigits,
    derivative_method::AbstractDerivativeMethod = DefaultDerivativeMethod]
)::IndependentParameter
```

適切な情報を与えると、[`IndependentParameter`](@ref) を返します。これは `JuMP.build_variable` に類似しています。supports が domain に関連する境界を違反する場合はエラーが発生します。これは主に [`@infinite_parameter`](@ref) のためのヘルパーメソッドとして機能することを意図しています。ここで `derivative_method` は、この無限パラメータに関して取られる導関数に適用される数値評価方法を指定します。

**例**

```julia-repl
julia> param = build_parameter(error, IntervalDomain(0, 3), supports = Vector(0:3));
```
