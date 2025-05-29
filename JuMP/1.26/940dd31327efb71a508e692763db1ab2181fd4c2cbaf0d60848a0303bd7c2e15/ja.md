```
fix(v::GenericVariableRef, value::Number; force::Bool = false)
```

変数を値に固定します。既存の固定制約がある場合はそれを更新し、そうでない場合は新しいものを作成します。

変数がすでに変数の境界を持っていて、`force=false`の場合、`fix`を呼び出すとエラーが発生します。`force=true`の場合、既存の変数の境界は削除され、固定制約が追加されます。[`unfix`](@ref)を呼び出した後、変数には境界がなくなります。

他に[`FixRef`](@ref)、[`is_fixed`](@ref)、[`fix_value`](@ref)、[`unfix`](@ref)も参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_fixed(x)
false

julia> fix(x, 1.0)

julia> is_fixed(x)
true
```

```jldoctest
julia> model = Model();

julia> @variable(model, 0 <= x <= 1);

julia> is_fixed(x)
false

julia> fix(x, 1.0; force = true)

julia> is_fixed(x)
true
```
