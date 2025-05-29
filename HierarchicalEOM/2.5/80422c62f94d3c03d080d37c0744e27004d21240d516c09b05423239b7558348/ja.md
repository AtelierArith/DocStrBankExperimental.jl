```
BosonBath(op, η, γ, δ=0.0; combine=true)
```

実数部と虚数部の相関関数が結合される場合のBosonBathオブジェクトを生成します。

$$
\begin{aligned}
C(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega)\left[n(\omega)e^{i\omega \tau}+(n(\omega)+1)e^{-i\omega \tau}\right]\\
&=\sum_i \eta_i \exp(-\gamma_i \tau),
\end{aligned}
$$

ここで、$J(\omega)$はバスのスペクトル密度であり、$n(\omega)$はボース-アインシュタイン分布を表します。

# パラメータ

  * `op::QuantumObject` : システム結合演算子で、エルミートでなければならず、フェルミオン系の場合は電荷保存に適合するために偶数対称である必要があります。
  * `η::Vector{Ti<:Number}` : バス相関関数$C(\tau)$における係数$\eta_i$。
  * `γ::Vector{Tj<:Number}` : バス相関関数$C(\tau)$における係数$\gamma_i$。
  * `δ::Number` : 近似の不一致（デフォルトは`0.0`）で、HEOM行列に終端子を追加するために使用されます（関数: addTerminatorを参照）。
  * `combine::Bool` : 同じ周波数の指数展開項を結合するかどうか。デフォルトは`true`です。
