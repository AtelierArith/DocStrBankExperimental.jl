```
thresh_soft(x::Real, delta)
```

ソフトしきい値関数。

  * `x` : 変換する値。
  * `delta` : しきい値の範囲。

返される値は：

  * sign(`x`) * max(0, abs(`x`) - `delta`)

ここで、delta >= 0。

## 例

```julia
using Jchemo, CairoMakie 

delta = .7
thresh_soft(3, delta)

x = LinRange(-2, 2, 100)
y = thresh_soft.(x, delta)
lines(x, y; axis = (xlabel = "x", ylabel = "f(x)"))
```
