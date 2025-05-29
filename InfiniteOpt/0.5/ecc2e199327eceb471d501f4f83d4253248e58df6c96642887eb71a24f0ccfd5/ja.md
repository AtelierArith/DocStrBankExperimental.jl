```
evaluate(dref::DerivativeRef)::Nothing
```

`dref`を数値的に評価するには、その補助導関数制約（例：コレクション方程式）を計算し、それをモデルに追加します。通常の使用では、このメソッドを直接呼び出さず、代わりにTranscriptionOptがこれらの方程式を処理することを推奨します。使用される導関数メソッドに対して`evaluate_derivative`が定義されていない場合はエラーが発生します。

結果として得られる制約には`derivative_constraints`を介してアクセスできます。

**例**

```julia-repl
julia> m = InfiniteModel(); @infinite_parameter(m, t in [0,2]); @variable(m, T, Infinite(t));

julia> dref = @deriv(T,t)
∂/∂t[T(t)]

julia> add_supports(t, [0, 0.5, 1, 1.5, 2])

julia> evaluate(dref)

julia> derivative_constraints(dref)
Feasibility
4-element Array{InfOptConstraintRef,1}:
 0.5 ∂/∂t[T(t)](0.5) - T(0.5) + T(0) = 0.0
 0.5 ∂/∂t[T(t)](1) - T(1) + T(0.5) = 0.0
 0.5 ∂/∂t[T(t)](1.5) - T(1.5) + T(1) = 0.0
 0.5 ∂/∂t[T(t)](2) - T(2) + T(1.5) = 0.0
```
