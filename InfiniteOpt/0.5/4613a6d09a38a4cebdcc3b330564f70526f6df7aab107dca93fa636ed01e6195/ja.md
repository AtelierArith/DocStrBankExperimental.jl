```
@deriv(expr, pref_expr1[, ...]
       )::Union{JuMP.AbstractJuMPScalar, Float64}
```

式の構築に対してより効率的であり、`pref_expr`を介して記号的微分演算子パラメータ定義を可能にする[`deriv`](@ref)のマクロバリアントです。`deriv`と同様に、`expr`は任意のInfiniteOpt式であり、`pref_expr`によって示された無限パラメータに関してその導関数を取るために適切な微積分ルールが`expr`に適用されます。結果として得られる導関数式には、必要に応じてInfiniteModelに作成され追加された個々の導関数が含まれます。ここで各`pref_expr`引数は次の形式を取ることができます：

  * `pref::GeneralVariableRef`: 個々の無限パラメータ参照
  * `(pref::GeneralVariableRef)^(p::Int)`: `p`回適用された無限パラメータ。

したがって、構文`@deriv(expr, pref^2)`は`@deriv(expr, pref, pref)`と同等です。

`pref_expr`が認識されない構文である場合、無限パラメータが与えられていない場合、または指定されたパラメータのいずれかが無限でない場合、エラーが発生します。

**例**

```julia-repl
julia> @infinite_parameter(m, t in [0, 1])
t

julia> @variable(m, x, Infinite(t))
x(t)

julia> @variable(m, z)
z

julia> deriv_expr = @deriv(x^2 + z, t^2)
2 ∂/∂t[∂/∂t[x(t)]]*x(t) + 2 ∂/∂t[x(t)]²
```
