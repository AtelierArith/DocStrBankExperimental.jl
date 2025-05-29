```julia
struct AdamsBashforthCrankNicolsonMethod{T, M} <: IncompressibleNavierStokes.AbstractODEMethod{T}
```

IMEX AB-CN: 明示的対流に対するアダムス-バシュフォース（パラメータ `α₁` と `α₂`）と、暗黙的拡散に対するクランク-ニコルソン（暗黙性 `θ`）。この方法は `θ = 1/2` のとき二次の精度を持ちます。

LHS行列のLU分解は、時間ステップが変わるたびに計算されます。

明示的な方法とは対照的に、前の時間ステップからの圧力は速度の精度に影響を与えます。

ここでは、時間ステップ $\Delta t$ が一定であることを要求します。この方法は、対流項にアダムス-バシュフォースを使用し、拡散および外力項にクランク-ニコルソンステッピングを使用します。時間 $t_0$ における速度場 $u_0 = u(t_0)$ と、その前の値 $u_{-1} = u(t_0 - \Delta t)$ があるとき、時間 $t = t_0 + \Delta t$ における予測された速度場 $u$ は、まず仮の速度を計算することによって定義されます：

$$
\begin{split}
\frac{v - u_0}{\Delta t}
& = - (\alpha_0 C(u_0, t_0) + \alpha_{-1} C(u_{-1}, t_{-1})) \\
& + \theta (D u_0 + y_D(t_0)) + (1 - \theta) (D v + y_D(t)) \\
& + \theta f(t_0) + (1 - \theta) f(t) \\
& - (G p_0 + y_G(t_0)),
\end{split}
$$

ここで、$\theta \in [0, 1]$ はクランク-ニコルソンパラメータ（$\theta = \frac{1}{2}$ は二次収束のため）、$(\alpha_0, \alpha_{-1}) = \left( \frac{3}{2}, -\frac{1}{2} \right)$ はアダムス-バシュフォース係数であり、$v$ はまだ発散のない仮の速度です。$v$ を含む項を左辺にまとめると、次のようになります。

$$
\begin{split}
\left( \frac{1}{\Delta t} I - (1 - \theta) D \right) v
& = \left(\frac{1}{\Delta t} I - \theta D \right) u_0 \\
& - (\alpha_0 C(u_0, t_0) + \alpha_{-1} C(u_{-1}, t_{-1})) \\
& + \theta y_D(t_0) + (1 - \theta) y_D(t) \\
& + \theta f(t_0) + (1 - \theta) f(t) \\
& - (G p_0 + y_G(t_0)).
\end{split}
$$

与えられた右辺を使用して、正定値行列 $\left( \frac{1}{\Delta t} I - \theta D \right)$ を逆にすることによって $v$ を計算できます。$\Delta t$ が一定であると仮定すると、時間ステッピングを開始する前にこの行列のコレスキー分解を事前計算できます。

次に、次のようにして圧力差 $\Delta p$ を解決します。

$$
L \Delta p = W \frac{M v + y_M(t)}{\Delta t} - W M (y_G(t) - y_G(t_0)),
$$

その後、発散のない速度 $u$ を強制することができます：

$$
u = v - \Delta t (G \Delta p + y_G(t) - y_G(t_0)).
$$

対応する圧力の一次精度の予測は $p = p_0 + \Delta p$ です。しかし、この圧力は次の時間ステップで再利用されるため、一次誤差が蓄積されないように追加の圧力解決を行います。結果として得られる圧力 $p$ は、$u$ と同じ次数の精度になります。

## フィールド

  * `α₁`
  * `α₂`
  * `θ`
  * `p_add_solve`
  * `method_startup`

```
