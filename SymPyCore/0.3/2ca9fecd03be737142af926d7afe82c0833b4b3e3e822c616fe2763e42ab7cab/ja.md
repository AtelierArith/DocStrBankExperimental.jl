```
solve
```

`solve`を使用して代数方程式を解きます。

# 拡張ヘルプ

例:

```jldoctest mathfuns
julia> using SymPyPythonCall


julia> @syms x y a b c d
(x, y, a, b, c, d)

julia> solve(x^2 + 2x + 1, x) # [-1]
1-element Vector{Sym{PythonCall.Py}}:
 -1

julia> solve(x^2 + 2a*x + a^2, x) # [-a]
1-element Vector{Sym{PythonCall.Py}}:
 -a

julia> u = solve([a*x + b*y-3, c*x + b*y - 1], [x,y]); show(u[x])
2/(a - c)
```

!!! note
    `solve`を使用した非常に良い例は、Xing Shi Caiによる[Napoleonの定理](https://en.wikipedia.org/wiki/Napoleon%27s_theorem)に関する[ブログ](https://newptcai.github.io/euclidean-plane-geometry-with-julia.html)のエントリーです。


!!! note "システム"
    複数の方程式がある場合は、ベクトルではなくタプルを使用してください。

