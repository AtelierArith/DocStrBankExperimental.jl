```
get_variables(e, varlist = nothing; sort::Bool = false)
```

`e`に現れる変数のベクトルを返します。オプションで`varlist`に制限することができます。

返される変数は`Num`型でラップされていないことに注意してください。

# 例

```jldoctest
julia> @variables t x y z(t);

julia> Symbolics.get_variables(x + y + sin(z); sort = true)
3-element Vector{SymbolicUtils.BasicSymbolic}:
 x
 y
 z(t)

julia> Symbolics.get_variables(x - y; sort = true)
2-element Vector{SymbolicUtils.BasicSymbolic}:
 x
 y
```
