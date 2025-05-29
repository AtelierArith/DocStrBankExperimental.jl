```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Infinite)::InfiniteVariable{GeneralVariableRef}
```

`info` と `var_type` に基づいて無限変数を構築して返します。`var_type` に含まれる無限パラメータ参照が無効な場合はエラーが発生します。詳細については [`Infinite`](@ref) を参照してください。

**例**

```julia-repl
julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));
```
