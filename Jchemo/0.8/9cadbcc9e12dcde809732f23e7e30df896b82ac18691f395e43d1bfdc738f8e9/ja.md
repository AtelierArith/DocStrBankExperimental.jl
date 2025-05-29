```
loessr(; kwargs...)
loessr(X, y; kwargs...)
```

ローカル加重回帰モデル（LOESS）を計算します。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量yデータ (n)。

キーワード引数：

  * `span` : ローカルフィッティングのための近傍選択のウィンドウ（平滑化のレベル）、通常は[0, 1]（割合）内。
  * `degree` : ローカルフィッティングのための多項式の次数。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正標準偏差でスケーリングされます。

この関数は、パッケージ`Loess.jl`を使用してLOESSモデルをフィットします。

`span`の値が小さいほど、フィッティングにおけるローカルコンテキストが小さくなります（平滑化が少なくなります）。

## 参考文献

https://github.com/JuliaStats/Loess.jl

Cleveland, W. S. (1979). Robust locally weighted regression and smoothing  scatterplots. Journal of the American statistical association, 74(368), 829-836.  DOI: 10.1080/01621459.1979.10481038

Cleveland, W. S., & Devlin, S. J. (1988). Locally weighted regression: an approach  to regression analysis by local fitting. Journal of the American statistical association,  83(403), 596-610. DOI: 10.1080/01621459.1988.10478639

Cleveland, W. S., & Grosse, E. (1991). Computational methods for local regression.  Statistics and computing, 1(1), 47-62. DOI: 10.1007/BF01890836

## 例

```julia
using Jchemo, CairoMakie

####### sinc(x)関数のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 で説明されている 
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
model = loessr(span = 1 / 3) 
fit!(model, x, y)
pred = predict(model, x).pred 
f = Figure(size = (700, 300))
ax = Axis(f[1, 1], xlabel = "x", ylabel = "y")
scatter!(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred); label = "Loess")
f[1, 2] = Legend(f, ax, framevisible = false)
f
```
