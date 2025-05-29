```
BosonBathRWA(op, η_absorb, γ_absorb, η_emit, γ_emit, δ=0.0)
```

RWA（回転波近似）を適用した系とボソンバスとの相互作用を持つBosonBathオブジェクトを生成するための関数です。

$$
\begin{aligned}
C^{\nu=+}(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega) n(\omega) e^{i\omega \tau}\\
&=\sum_i \eta_i^{\nu=+} \exp(-\gamma_i^{\nu=+} \tau),\\
C^{\nu=-}(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega) (1+n(\omega)) e^{-i\omega \tau}\\
&=\sum_i \eta_i^{\nu=-} \exp(-\gamma_i^{\nu=-} \tau),
\end{aligned}
$$

ここで、$\nu=+$（$\nu=-$）は吸収（放出）プロセスを表し、$J(\omega)$はバスのスペクトル密度、$n(\omega)$はボース-アインシュタイン分布です。

# パラメータ

  * `op::QuantumObject` : 系とボソンバスの相互作用に従った系の消滅演算子。
  * `η_absorb::Vector{Ti<:Number}` : 吸収バス相関関数$C^{\nu=+}(\tau)$の係数$\eta_i$。
  * `γ_absorb::Vector{Tj<:Number}` : 吸収バス相関関数$C^{\nu=+}(\tau)$の係数$\gamma_i$。
  * `η_emit::Vector{Tk<:Number}` : 放出バス相関関数$C^{\nu=-}(\tau)$の係数$\eta_i$。
  * `γ_emit::Vector{Tl<:Number}` : 放出バス相関関数$C^{\nu=-}(\tau)$の係数$\gamma_i$。
  * `δ::Number` : HEOMLS行列に終端子を追加するために使用される近似の不一致（デフォルトは`0.0`）。
