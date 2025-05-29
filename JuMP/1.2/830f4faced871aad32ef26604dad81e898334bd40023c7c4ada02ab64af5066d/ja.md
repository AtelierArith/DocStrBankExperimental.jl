```
primal_feasibility_report(
    point::Function,
    model::Model;
    atol::Float64 = 0.0,
    skip_missing::Bool = false,
)
```

`primal_feasibility_report` の形式の一つで、最初の引数として関数が渡され、第二の引数として辞書が渡されるのではありません。

## 例

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1);

julia> primal_feasibility_report(model) do v
           return value(v)
       end
Dict{Any,Float64} with 1 entry:
    x ≥ 0.5 => 0.3
```
