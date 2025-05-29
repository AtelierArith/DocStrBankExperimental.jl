```
function_string(
    mode::MIME,
    func::Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
)
```

`func`を印刷モード`mode`を使用して表す`String`を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> function_string(MIME("text/plain"), 2 * x + 1)
"2 x + 1"
```
