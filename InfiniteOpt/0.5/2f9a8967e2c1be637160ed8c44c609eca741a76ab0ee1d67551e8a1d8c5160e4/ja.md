```
deriv(expr::JuMP.AbstractJuMPScalar, pref1::GeneralVariableRef[, ....]
      )::Union{JuMP.AbstractJuMPScalar, Float64}
```

適切な微積分の手法を適用して、`expr` の無限パラメータ `pref1`, `pref2`, などに関しての導関数式を定義し、返します。これは、適切に個々の [`Derivative`](@ref) を構築して追加することを暗黙的に行います。無限パラメータが与えられない場合や、パラメータが無限でない場合はエラーになります。

**例**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1])
t

julia> @variable(m, x, Infinite(t))
x(t)

julia> @variable(m, z)
z

julia> deriv_expr = deriv(x^2 + z, t, t)
2 ∂/∂t[∂/∂t[x(t)]]*x(t) + 2 ∂/∂t[x(t)]²
```
