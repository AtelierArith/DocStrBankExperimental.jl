```
fix([context::AbstractContext,] values::NamedTuple)
fix([context::AbstractContext]; values...)
```

`values`が空でない場合は`values`と`context`を持つ`FixedContext`を返し、そうでない場合はデフォルトで[`DefaultContext`](@ref)である`context`を返します。

参照: [`unfix`](@ref)
