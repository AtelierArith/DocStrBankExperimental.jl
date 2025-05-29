```
savgk(nhwindow::Int, degree::Int, deriv::Int)
```

サヴィッツキー・ゴレイフィルタのカーネルを計算します。

  * `nhwindow` : 半ウィンドウのポイント数 (>= 1)。
  * `degree` : スムージング多項式の次数で、1 <= `degree` <= 2 * nhwindow。
  * `deriv` : 微分の次数で、0 <= `deriv` <= degree。

カーネルのサイズは奇数です (npoint = 2 * nhwindow + 1):

  * x[-nhwindow], x[-nhwindow+1], ..., x[0], ...., x[nhwindow-1], x[nhwindow]。

`deriv` = 0 の場合、微分は行われず（多項式スムージングのみ）、結果が得られます。

`degree` = 0（すなわち単純移動平均）の場合は、関数によって許可されていません。

## 参考文献

Luo, J., Ying, K., Bai, J., 2005. Savitzky–Golay smoothing and differentiation filter for even number data. Signal Processing 85, 1429–1434. https://doi.org/10.1016/j.sigpro.2005.02.002

## 例

```julia
using Jchemo
res = savgk(21, 3, 2)
@names res
res.S 
res.G 
res.kern
```
