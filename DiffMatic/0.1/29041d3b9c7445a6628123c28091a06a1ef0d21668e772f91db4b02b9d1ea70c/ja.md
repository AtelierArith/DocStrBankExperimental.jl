```
to_std(expr; format = StdStr())
```

式 `expr` を標準表記に変換します。

  * `format`: 出力形式。次のいずれかです：

      * [`StdStr`](@ref): 文字列形式。
      * [`JuliaFunc`](@ref): Julia 関数。

例：

```jldoctest to_std
@matrix A
@vector x

to_std(gradient(x' * A * x, x))

# 出力

"Aᵀx + Ax"
```

```julia
to_std(gradient(x' * A * x, x); format = JuliaFunc())

# 出力

quote
    #= ... =#
    function generated_function(A, x)
        #= ... =#
        #= ... =#
        return transpose(A) * x + A * x
    end
end
```
