```
thresh_hard(x::Real, delta)
```

ハードしきい値関数。

  * `x` : 変換する値。
  * `delta` : しきい値の範囲。

返される値は：

  * abs(`x`) > `delta` ? `x` : 0

ここで delta >= 0。

## 例

```julia
using Jchemo, CairoMakie 

delta = .7
thresh_hard(3, delta)

x = LinRange(-2, 2, 500)
y = thresh_hard.(x, delta)
lines(x, y; axis = (xlabel = "x", ylabel = "f(x)"))
```
