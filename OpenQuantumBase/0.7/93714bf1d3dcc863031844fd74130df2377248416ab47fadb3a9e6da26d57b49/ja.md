```
q_translate(h::String; sp = false)
```

文字列 `h` を多量子ビットパウリ行列の総和として表現し、その数値形式に変換します。`sp` が true に設定されている場合は、スパース行列を生成します。

# 例

```julia-repl
julia> q_translate("X+2.0Z")
2×2 Array{Complex{Float64},2}:
 2.0+0.0im   1.0+0.0im
 1.0+0.0im  -2.0+0.0im
```
