```
VehicleTracking(y::Matrix{Fl}, ρ::Fl, H::Matrix{Fl}, Q::Matrix{Fl}) where Fl
```

車両追跡の例は、ハイパーパラメータがないモデルを示しており、ユーザーはパラメータ $\rho$, $H$ および $Q$ を定義し、モデルは予測された速度と位置を提供します。この場合、$y_t$ は、時刻 $t$ における二次元平面上の車両の位置の汚染された測定値を表す $2 \times 1$ の観測ベクトルです。

各次元の位置と速度は車両の状態を構成します。$x_t^{(d)}$ を軸 $d$ 上の位置、$\dot{x}^{(d)}_t$ を時刻 $t$ における軸 $d$ 上の速度と呼びましょう。さらに、$\eta^{(d)}_t$ を軸 $d$ 上の入力駆動力とし、これは状態ノイズとして作用します。単一の次元について、車両の動力学を次のように記述できます。

$$
\begin{equation}
    \begin{aligned}
        & x_{t+1}^{(d)} = x_t^{(d)} + \Big( 1 - \frac{\rho \Delta_t}{2} \Big) \Delta_t \dot{x}^{(d)}_t + \frac{\Delta^2_t}{2} \eta_t^{(d)}, \\
        & \dot{x}^{(d)}_{t+1} = (1 - \rho) \dot{x}^{(d)}_{t} + \Delta_t \eta^{(d)}_t,
    \end{aligned}\label{eq_control}
\end{equation}
$$

動的システムを次のように状態空間モデルとして表現できます。

$$
\begin{align*} 
    y_t &= \begin{bmatrix} 1 & 0 & 0 & 0 \\ 0 & 0 & 1 & 0 \end{bmatrix} \alpha_{t+1} + \varepsilon_t, \\
    \alpha_{t+1} &= \begin{bmatrix} 1 & (1 - \tfrac{\rho \Delta_t}{2}) \Delta_t & 0 & 0 \\ 0 & (1 - \rho) & 0 & 0 \\ 0 & 0 & 1 & (1 - \tfrac{\rho \Delta_t}{2}) \\ 0 & 0 & 0 & (1 - \rho) \end{bmatrix} \alpha_{t} + \begin{bmatrix} \tfrac{\Delta^2_t}{2} & 0 \\ \Delta_t & 0 \\ 0 & \tfrac{\Delta^2_t}{2} \\ 0 & \Delta_t \end{bmatrix} \eta_{t},
\end{align*}
$$

詳細については [Vehicle tracking](@ref) を参照してください。
