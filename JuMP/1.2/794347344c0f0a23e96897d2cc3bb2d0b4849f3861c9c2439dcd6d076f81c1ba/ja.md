```
fix(v::VariableRef, value::Number; force::Bool = false)
```

変数を値に固定します。既存の固定制約がある場合はそれを更新し、そうでない場合は新しい制約を作成します。

変数にすでに変数の境界があり、`force=false`の場合、`fix`を呼び出すとエラーが発生します。`force=true`の場合、既存の変数の境界は削除され、固定制約が追加されます。[`unfix`](@ref)を呼び出した後、変数には境界がなくなります。

他にも[`FixRef`](@ref)、[`is_fixed`](@ref)、[`fix_value`](@ref)、[`unfix`](@ref)があります。
