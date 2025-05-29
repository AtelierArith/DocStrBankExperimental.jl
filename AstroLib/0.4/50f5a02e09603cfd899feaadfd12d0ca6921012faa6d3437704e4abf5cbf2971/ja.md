```
trueanom(E, e) -> 真の異常
```

### 目的

離心率 $e$ と偏心異常 $E$ を持つ楕円軌道の粒子の真の異常を計算します。

### 説明

二体問題において、[ケプラーの方程式](https://en.wikipedia.org/wiki/Kepler%27s_equation) が解かれ、$E(t)$ が決定されると、時間 $t$ における楕円軌道上の物体の極座標 $(r(t), θ(t))$ は次のように与えられます。

$$
θ(t) = 2 \arctan \left( \sqrt{\frac{1 + e}{1 - e}} \tan\frac{E(t)}{2} \right)
$$

$$
r(t) = \frac{a(1 - e^2)}{1 + e\cos(θ(t) - θ_0)}
$$

ここで、$a$ は軌道の半長軸、$θ_0$ は時間 $t = t_0$ における角度座標の値です。

### 引数

  * `E`: 偏心異常。
  * `e`: 楕円運動領域における離心率 ($0 ≤ e ≤ 1$)

### 出力

真の異常。

### 例

離心率 $e = 0, 0.5, 0.9$ に対する平均異常の関数として真の異常をプロットします。プロットには [Plots.jl](https://github.com/JuliaPlots/Plots.jl/) を使用します。

```julia
using Plots
M = range(0, stop=2pi, length=1001)[1:end-1];
p = plot()
for ecc in (0, 0.5, 0.9)
    plot!(p, M, mod2pi.(trueanom.(kepler_solver.(M, ecc), ecc)))
end
p
```

### 注意

偏心異常は [`kepler_solver`](@ref) 関数を使って計算できます。
