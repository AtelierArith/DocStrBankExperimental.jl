```
set_lower_bound(v::VariableRef, lower::Number)
```

変数の下限を設定します。存在しない場合は、新しい下限制約を作成します。

関連情報として、[`LowerBoundRef`](@ref)、[`has_lower_bound`](@ref)、[`lower_bound`](@ref)、[`delete_lower_bound`](@ref)を参照してください。
