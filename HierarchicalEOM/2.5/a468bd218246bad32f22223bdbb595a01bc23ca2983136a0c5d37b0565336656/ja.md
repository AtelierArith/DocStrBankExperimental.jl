```
BosonBath(op, η_real, γ_real, η_imag, γ_imag, δ=0.0; combine=true)
```

相関関数が実部と虚部に分かれる場合のBosonBathオブジェクトを生成します。

$$
\begin{aligned}
C(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega)\left[n(\omega)e^{i\omega \tau}+(n(\omega)+1)e^{-i\omega \tau}\right]\\
&=\sum_i \eta_i \exp(-\gamma_i \tau),
\end{aligned}
$$

ここで、$J(\omega)$はバスのスペクトル密度であり、$n(\omega)$はボース-アインシュタイン分布を表します。

$$
\gamma_i \neq \gamma_i^*
$$

の場合、$C(\tau)$を実部 (R) と虚部 (I) にさらに分解することでHEOMの閉じた形を得ることができます。

$$
C(\tau)=\sum_{u=\textrm{R},\textrm{I}}(\delta_{u, \textrm{R}} + i\delta_{u, \textrm{I}})C^{u}(\tau)
$$

ここで、$\delta$はクロネッカーのデルタ関数であり、$C^{u}(\tau)=\sum_i \eta_i^u \exp(-\gamma_i^u \tau)$です。

# パラメータ

  * `op::QuantumObject` : システム結合演算子で、エルミートである必要があり、フェルミオン系の場合は電荷保存と互換性があるように偶数対称でなければなりません。
  * `η_real::Vector{Ti<:Number}` : バス相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\eta_i$。
  * `γ_real::Vector{Tj<:Number}` : バス相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\gamma_i$。
  * `η_imag::Vector{Tk<:Number}` : バス相関関数の虚部 $C^{u=\textrm{I}}$ における係数 $\eta_i$。
  * `γ_imag::Vector{Tl<:Number}` : バス相関関数の虚部 $C^{u=\textrm{I}}$ における係数 $\gamma_i$。
  * `δ::Number` : HEOM行列に終端子を追加するために使用される近似の不一致 (デフォルトは `0.0`)。
  * `combine::Bool` : 同じ周波数の指数展開項を結合するかどうか。デフォルトは `true`。
