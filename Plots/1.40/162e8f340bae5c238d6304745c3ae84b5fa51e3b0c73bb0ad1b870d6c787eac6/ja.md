```
surface(x,y,z)
surface!(x,y,z)
```

3Dサーフェスプロットを描画します。

# 例

```julia-repl
julia> using LinearAlgebra
julia> x = y = range(-3, stop = 3, length = 100)
julia> surface(x, y, (x, y) -> sinc(norm([x, y])))
```
