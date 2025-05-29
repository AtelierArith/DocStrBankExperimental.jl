```
merge_params(df_exp::Union{Nothing, DataFrame}, df_setup::Union{Nothing, DataFrame}, row::Integer) → (;nt, nt_exp, nt_setup, nt_unitless)
```

Merges default parameters and units from `df_setup` with the parameter in the given row of `df_exp`, and returns them as NamedTuple of NamedTuples.  Actually only the `nt` field of the returned value is used.

Function `merge_params` is public.

# Examples

```julia-repl
julia> m = GivEmXL.merge_params(df_exp, df_setup, 1);
julia> m.nt
(area = 0.5 cm², Vunit = mV, timeunit = s, Cunit = nF, R = 5 GΩ, t_start = 1 s, t_stop = 4 s, ϵ = 3.7, no = 1, plot_annotation = "first discharge", comment = "first discharge – 1")
```
