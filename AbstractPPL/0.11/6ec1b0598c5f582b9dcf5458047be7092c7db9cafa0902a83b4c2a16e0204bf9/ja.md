```
inspace(vn::Union{VarName, Symbol}, space::Tuple)
```

`vn`の変数シンボルが`space`に含まれているかを確認します。空のタプルはすべての変数を含む「普遍空間」としてカウントされます。包含関係（[`subsumes`](@ref)を参照）も尊重されます。

## 例

```jldoctest
julia> inspace(@varname(x[1][2:3]), ())
true

julia> inspace(@varname(x[1][2:3]), (:x,))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x),))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[1:10]), :y))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[:][2:4]), :y))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[1:10]),))
true
```
