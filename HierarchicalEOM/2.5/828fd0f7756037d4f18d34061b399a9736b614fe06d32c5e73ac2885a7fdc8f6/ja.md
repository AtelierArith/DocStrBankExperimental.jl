```
bosonReal(op, η_real, γ_real)
```

バス相関関数の実部 $C^{u=\textrm{R}}$ のためのボソンバスを生成します。

# パラメータ

  * `op::QuantumObject` : システム結合演算子で、エルミートである必要があり、フェルミオン系の場合は電荷保存と互換性を持つために偶数対称でなければなりません。
  * `η_real::Vector{Ti<:Number}` : バス相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\eta_i$ 。
  * `γ_real::Vector{Tj<:Number}` : バス相関関数の実部 $C^{u=\textrm{R}}$ における係数 $\gamma_i$ 。
