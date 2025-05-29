```
struct SymbolCache
function SymbolCache(vars, [params, [indepvars]]; defaults = Dict(), timeseries_parameters = nothing)
```

変数、パラメータ、および独立変数のコレクションのインデックスプロバイダインターフェースを実装する構造体です。 `vars` と `params` は配列として指定することができ（この場合、シンボルのインデックスは配列内のインデックスになります）、またはシンボルをインデックスにマッピングする `AbstractDict` として指定することもできます。少なくとも1つの独立変数を含む場合、時間依存と見なされます。

`is_observed(::SymbolCache, sym)` に対して `true` を返します、もし `sym isa Union{Expr, Array{Expr}, Tuple{Vararg{Expr}}` であれば。関数は、`SymbolCache` 内の変数を含む `Expr` に対して `observed` を使用して生成することができます、もしそれが最大1つの独立変数を持つ場合。

`defaults` は、変数および/またはパラメータをそのデフォルト初期値にマッピングする `AbstractDict` です。デフォルト初期値は、他の変数/パラメータまたはそれらの式であることもできます。 `timeseries_parameters` は、`params` 内の時系列パラメータをその [`ParameterTimeseriesIndex`](@ref) インデックスにマッピングする `AbstractDict` です。

独立変数は、システムに独立変数が1つしかない場合、単一の変数を含む配列の代わりに単一のシンボリック変数として指定することができます。
