```
merge_params(df_exp::Union{Nothing, DataFrame}, df_setup::Union{Nothing, DataFrame}, row::Integer) → (;nt, nt_exp, nt_setup, nt_unitless)
```

`df_setup`からのデフォルトパラメータと単位を`df_exp`の指定された行のパラメータとマージし、それらをNamedTupleのNamedTuplesとして返します。実際には、返される値の`nt`フィールドのみが使用されます。

関数`merge_params`は公開されています。

# 例

```julia-repl
julia> m = GivEmXL.merge_params(df_exp, df_setup, 1);
julia> m.nt
(area = 0.5 cm², Vunit = mV, timeunit = s, Cunit = nF, R = 5 GΩ, t_start = 1 s, t_stop = 4 s, ϵ = 3.7, no = 1, plot_annotation = "first discharge", comment = "first discharge – 1")
```
