```
build_parameter(_error::Function, value::Real)::FiniteParameter
```

適切な情報が与えられた場合、[`FiniteParameter`](@ref)を返します。これは`JuMP.build_variable`に類似しています。主に[`@finite_parameter`](@ref)のヘルパーメソッドとして機能することを意図しています。

**例**

```jldoctest; setup = :(using InfiniteOpt)
julia> build_finite_parameter(error, 1)
FiniteParameter(1.0)
```
