```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::SemiInfinite)::SemiInfiniteVariable{GeneralVariableRef}
```

`info` と `var_type` に基づいて半無限変数を構築して返します。`var_type` に格納されている情報が無効な場合はエラーが発生します。詳細については [`SemiInfinite`](@ref) を参照してください。

**例**

```julia-repl
julia> y
y(t, x)

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> semi_inf_var = build_variable(error, info, SemiInfinite(y, t, 0));
```
