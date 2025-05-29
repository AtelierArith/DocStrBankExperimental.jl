```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Deriv)::InfiniteVariable{GeneralVariableRef}
```

`info` と `var_type` に基づいて一次導関数を構築して返します。`var_type` の情報が無効な場合はエラーが発生します。詳細については [`Deriv`](@ref) を参照してください。

**例**

```julia-repl
julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> deriv_var = build_variable(error, info, Deriv(y, t));
```
