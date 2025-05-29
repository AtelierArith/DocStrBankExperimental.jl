```
Non_negative()
```

非負の数にマッピングする関数とその逆関数を返します。放物線を使用します。

# 例

```julia-repl
julia> p, p_inv = Non_negative()
(DeconvOptim.var"#5#7"(), DeconvOptim.var"#6#8"())

julia> x = [-1, 2, -3]
3-element Array{Int64,1}:
 -1
  2
 -3

julia> p(x)
3-element Array{Int64,1}:
 1
 4
 9

julia> p_inv(p(x))
3-element Array{Float64,1}:
 1.0
 2.0
 3.0
```
