```
pull_vars(::Num)
pull_vars(::Vector{Num})
pull_vars(::Equation)
pull_vars(::Vector{Equation})
```

式または方程式の右辺（または一連の方程式の右辺）からすべての変数/シンボルを抽出し、ソートします。変数はアルファベット順にソートされ、その後に [cv, cc, L, U] の順で、次に凸緩和のサブグラディエントの項と凹緩和のサブグラディエントの項が続きます。

# 例

```julia> @variables out, x, y, z
julia> func = out ~ z + 2*y - 3*x*z
julia> pull_vars(func)
3-element Vector{Num}:
 x
 y
 z
```
