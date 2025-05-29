```
JuMP.build_variable(_error::Function, info::JuMP.VariableInfo, 
                    var_type::Point)::InfiniteVariable{GeneralVariableRef}
```

`info` と `var_type` に基づいてポイント変数を構築して返します。`var_type` に格納されている情報が無効な場合はエラーが発生します。詳細については [`Point`](@ref) を参照してください。

**例**

```julia-repl
julia> y
y(t)

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> pt_var = build_variable(error, info, SemiInfinite(y, 0));
```
