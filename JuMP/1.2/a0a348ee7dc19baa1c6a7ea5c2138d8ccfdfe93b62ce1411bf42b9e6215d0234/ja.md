```
FixRef(v::VariableRef)
```

値 `v` を固定する制約への参照を返します。存在しない場合はエラーになります。

関連情報として [`is_fixed`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref) を参照してください。
