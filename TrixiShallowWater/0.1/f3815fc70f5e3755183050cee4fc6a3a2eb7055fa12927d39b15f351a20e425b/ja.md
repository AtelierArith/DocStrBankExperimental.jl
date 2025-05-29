```
ShallowWaterExnerEquations1D(;gravity, H0 = 0.0,
                             friction = ManningFriction(n = 0.0),
                             sediment_model,
                             porosity,
                             rho_f, rho_s)
```

一つの空間次元における浅水-エクスナー方程式の定式化であり、数学的エントロピー不等式を持っています。方程式は次のように与えられます。

$$
\begin{cases}
\partial_t h + \partial_x hv = 0, \\
\partial_t hv + \partial_x (hv^2) + gh\partial_x (h + h_b) + g\frac{1}{r}h_s\partial_x (rh + h_b) + \frac{\tau}{\rho_f} = 0,\\
\partial_t h_b + \partial_x q_s = 0,
\end{cases}
$$

未知の量は水と堆積物の高さ $h$, $h_b$ と速度 $v$ です。堆積物の流出量 $q_s(h, hv)$ は `sediment_model` によって決定され、活性堆積物の高さ $h_s = q_s / v$ を決定するために使用されます。さらに、$\tau$ は水-堆積物界面でのせん断応力を示し、`friction` モデルによって決定されます。重力加速度は $g$ で示され、$\rho_f$ と $\rho_s$ はそれぞれ流体と堆積物の密度です。密度比は $r = \rho_f / \rho_s$ で与えられ、流体密度 $\rho_f$ は堆積物密度 $\rho_s$ よりも小さいため、$0 < r < 1$ の範囲にあります。

保存変数である水の高さ $h$ は堆積物の高さ $h_b$ から測定されるため、全水高さを $H = h + h_b$ と定義します。

追加の量 $H_0$ は、初期条件を設定したり「静止湖」の良好なバランスをテストするために便利な全水高さの参照値を格納するために利用可能です。

エントロピー保存の定式化は、次の論文で導出されています：

  * E.D. Fernández-Nieto, T.M. de Luna, G. Narbona-Reina and J. de Dieu Zabsonré (2017) 任意の傾斜を持つ堆積床と関連するエネルギーを含むサン＝ヴェナン–エクスナー・モデルの正式な導出 [DOI: 10.1051/m2an/2016018](https://doi.org/10.1051/m2an/2016018)

```
