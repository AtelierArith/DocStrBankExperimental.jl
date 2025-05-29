```julia
check_unitary(𝐔; rtol, atol)

```

`𝐔`がユニタリ行列であるかをテストします。この関数は、$𝐔𝐔^†$と$𝐔^†𝐔$が$I$にどれだけ近いかを、相対誤差と絶対誤差を`rtol`、`atol`で与えてチェックします。

# 例

```julia-repl
julia> check_unitary(exp(-1.0im*5*0.5*σx))
true
```
