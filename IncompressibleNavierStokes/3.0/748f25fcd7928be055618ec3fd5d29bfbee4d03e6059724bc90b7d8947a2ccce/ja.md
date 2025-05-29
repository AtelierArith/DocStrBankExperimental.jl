```julia
struct OneLegMethod{T, M} <: IncompressibleNavierStokes.AbstractODEMethod{T}
```

対称性を保持する乱流の離散化に従った明示的なワンレッグβ法。詳細については、VerstappenとVeldman [Verstappen2003](@cite) [Verstappen1997](@cite) を参照してください。

ここでは、時間ステップ $\Delta t$ が一定であることを要求します。現在の時間 $t_0$ における速度 $u_0$ と圧力 $p_0$、および前の値 $u_{-1}$ と $p_{-1}$ が $t_{-1} = t_0 - \Delta t$ のときのものであるとし、まず "オフステップ" 値 $v = (1 + \beta) v_0 - \beta v_{-1}$ と $Q = (1 + \beta) p_0 - \beta p_{-1}$ を計算します。ここで、$\beta = \frac{1}{2}$ とします。

次に、仮の速度場 $\tilde{v}$ は次のように計算されます：

$$
\tilde{v} = \frac{1}{\beta + \frac{1}{2}} \left( 2 \beta u_0 - \left( \beta -
\frac{1}{2} \right) u_{-1} + \Delta t F(v, t) - \Delta t
(G Q + y_G(t)) \right).
$$

圧力補正 $\Delta p$ はポアソン方程式を解くことによって得られます：

$$
L \Delta p = \frac{\beta + \frac{1}{2}}{\Delta t} W (M \tilde{v} + y_M(t)).
$$

最後に、発散のない速度場は次のように与えられます：

$$
u = \tilde{v} - \frac{\Delta t}{\beta + \frac{1}{2}} G \Delta p,
$$

一方、二次精度の圧力は次のように与えられます：

$$
p = 2 p_0 - p_{-1} + \frac{4}{3} \Delta p.
$$

## フィールド

  * `β`
  * `p_add_solve`
  * `method_startup`
