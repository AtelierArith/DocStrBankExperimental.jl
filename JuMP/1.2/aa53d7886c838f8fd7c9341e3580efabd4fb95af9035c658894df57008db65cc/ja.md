```
set_upper_bound(v::VariableRef, upper::Number)
```

変数の上限を設定します。上限が存在しない場合は、上限制約を作成します。

関連情報としては、[`UpperBoundRef`](@ref)、[`has_upper_bound`](@ref)、[`upper_bound`](@ref)、[`delete_upper_bound`](@ref)があります。
