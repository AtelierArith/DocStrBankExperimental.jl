```
measure(expr::JuMP.AbstractJuMPScalar,
        data::AbstractMeasureData;
        [name::String = "measure"])::GeneralVariableRef
```

`expr`を`data`に従って評価する測定参照を返します。測定データ`data`は、測定がどのように評価されるかを決定します。通常、`DiscreteMeasureData`および`FunctionalDiscreteMeasureData`コンストラクタを`data`に使用できます。変数式`expr`には、`InfiniteOpt`変数、無限パラメータ、他の測定参照（つまり、測定はネスト可能）、および定数を含めることができます。通常、これは`JuMP.@expression`、`JuMP.@objective`、および`JuMP.@constraint`の中で、`sum`に似た方法で呼び出されます。測定は、[`build_optimizer_model!`](@ref)が呼び出されるか、[`expand`](@ref)または[`expand_all_measures!`](@ref)を介して展開されるまで、明示的には評価されません。

**例**

```julia-repl
julia> tdata = DiscreteMeasureData(t, [0.5, 0.5], [1, 2]);

julia> xdata = DiscreteMeasureData(xs, [0.5, 0.5], [[-1, -1], [1, 1]]);

julia> constr_RHS = @expression(model, measure(g - s + 2, tdata) + s^2)
measure{t}[g(t) - s + 2] + s²

julia> @objective(model, Min, measure(g - 1  + measure(T, xdata), tdata))
measure{xs}[g(t) - 1 + measure{xs}[T(t, x)]]
```
