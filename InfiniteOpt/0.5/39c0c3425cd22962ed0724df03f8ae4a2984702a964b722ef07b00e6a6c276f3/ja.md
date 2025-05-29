```
JuMP.set_name(pref::ScalarParameterRef, name::String)
```

`JuMP.set_name` 関数を拡張して無限パラメータに対応させます。`pref` に関連付ける新しい基本名を設定します。

**例**

```julia-repl
julia> set_name(t, "time")

julia> name(t)
"time"
```
