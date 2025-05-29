```
@syntax_pattern <syntax type> <syntax checker>
```

Bundle a syntax type as MLStyle pattern.

!!! tip
    this is not available in ExproniconLite since it depends on MLStyle's pattern matching functionality.


# Example

```julia
struct MyFunction
    ex :: Expr
    test_field :: Any
end

is_xxx(ex::Expr) = Meta.isexpr(ex, :function)
is_xxx(_) = false

julia> MyFunction(ex::Expr) = MyFunction(ex, :aaa)
julia> @syntax_pattern(MyFunction, is_xxx)

julia> @match :(function f() end) begin
        MyFunction(;test_field) => test_field
    end
:aaa
```
