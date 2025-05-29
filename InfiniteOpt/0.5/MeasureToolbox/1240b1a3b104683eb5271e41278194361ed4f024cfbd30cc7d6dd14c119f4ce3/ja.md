```
expect(expr::JuMP.AbstractJuMPScalar,
       prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef};
       [num_supports::Int = DefaultNumSupports])::GeneralVariableRef
```

`prefs` に関する期待値に基づいて `expr` の測定を行います。分布ドメインを持つ `prefs` に対しては、基本的に次のように等価です。

```julia
1/total_num_supports * support_sum(expr, prefs, label = WeightedSample)
```

したがって、これらのドメインタイプでは、`prefs` を生成時に作成する際に `num_supports` キーワードを指定することによって追加されたサポートのみを考慮します。他のサポートを組み込むには、[`integral`](@ref) を呼び出し、`weight_func` 引数を使用して確率密度関数を指定することを検討してください。

有界区間ドメイン上で定義された単一の無限パラメータの場合、構文は次のようになります。

```julia
    expect(expr::JuMP.AbstractJuMPScalar,
           prefs::GeneralVariableRef;
           [num_supports::Int = DefaultNumSupports,
           pdf::Function = (supp) -> 1 / (ub - lb)])::GeneralVariableRef
```

デフォルトの `pdf` の動作は、[`UniTrapezoid`](@ref) を使用して `pref` に関して `expr` のための積分の平均値定理を評価することに相当します。他の密度関数は `pdf` を介して指定できます。区間ドメインが有界でない場合はエラーが発生します。

単一の依存パラメータが与えられた場合、num_supports は 0 であるべきです。また、`expr` が単一の変数参照だけでない場合は、[`@expect`](@ref) を呼び出すことが推奨されます。

**例**

```julia-repl
julia> @infinite_parameter(model, x ~ Normal(), num_supports = 2)
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> meas = expect(f, x)
𝔼{x}[f(x)]

julia> expand(meas)
0.5 f(0.6791074260357777) + 0.5 f(0.8284134829000359)
```
