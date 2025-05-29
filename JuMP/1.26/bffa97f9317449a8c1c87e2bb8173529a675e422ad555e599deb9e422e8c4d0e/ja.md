```
primal_feasibility_report(
    point::Function,
    model::GenericModel{T};
    atol::T = zero(T),
    skip_missing::Bool = false,
) where {T}
```

`primal_feasibility_report` の形式の一つで、最初の引数として関数が渡され、第二の引数として辞書が渡されるのではありません。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1, start = 1.3);

julia> primal_feasibility_report(model) do v
           return start_value(v)
       end
Dict{Any, Float64} with 1 entry:
  x ≤ 1 => 0.3
```
