```
Ok{T}
```

`Result{T, E}`の成功状態で、型`T`のオブジェクトを保持します。便利のために、`Ok(x)`は適切な`Result type`に変換できるダミー値を作成します。

`Ok`とその鏡像である`Err`のインスタンスは直接構築することはできません。

参照: [`Err`](@ref)

```jldoctest
julia> function reciprocal(x::Int)::Result{Float64, String}
           iszero(x) && return Err("Division by zero")
           Ok(1 / x)
       end;

julia> reciprocal(4)
Result{Float64, String}(Ok(0.25))

julia> reciprocal(0)
Result{Float64, String}(Err("Division by zero"))
```
