```
bosonImag(op, η_imag, γ_imag)
```

虚数部分の相関関数 $C^{u=\textrm{I}}$ のボソンバスを生成します。

# パラメータ

  * `op::QuantumObject` : システム結合演算子で、エルミートである必要があり、フェルミオン系の場合は電荷保存と互換性があるように偶数対称でなければなりません。
  * `η_imag::Vector{Ti<:Number}` : バス相関関数の虚数部分 $C^{u=\textrm{I}}$ における係数 $\eta_i$ 。
  * `γ_imag::Vector{Tj<:Number}` : バス相関関数の虚数部分 $C^{u=\textrm{I}}$ における係数 $\gamma_i$ 。
