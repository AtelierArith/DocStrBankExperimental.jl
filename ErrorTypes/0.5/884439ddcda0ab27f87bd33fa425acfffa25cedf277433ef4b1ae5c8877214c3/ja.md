```
@unwrap_or(expr, exec)
```

`expr`を`Result`として評価します。もし`expr`がエラー値であれば、`exec`を評価してそれを返します。そうでなければ、`expr`にラップされた値を返します。

参照: [`@unwrap_error_or`](@ref)

# 例

```julia
julia> safe_inv(x)::Option{Float64} = iszero(x) ? none : Ok(1/x);

julia> function skip_inv_sum(it)
    sum = 0.0
    for i in it
        sum += @unwrap_or safe_inv(i) continue
    end
    sum
end;

julia> skip_inv_sum([2,1,0,1,2])
3.0
```
