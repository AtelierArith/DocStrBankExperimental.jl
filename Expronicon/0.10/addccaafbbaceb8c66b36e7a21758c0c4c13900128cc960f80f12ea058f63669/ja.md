```
@syntax_pattern <構文タイプ> <構文チェッカー>
```

MLStyleパターンとして構文タイプをバンドルします。

!!! tip
    これはMLStyleのパターンマッチング機能に依存しているため、ExproniconLiteでは利用できません。


# 例

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
