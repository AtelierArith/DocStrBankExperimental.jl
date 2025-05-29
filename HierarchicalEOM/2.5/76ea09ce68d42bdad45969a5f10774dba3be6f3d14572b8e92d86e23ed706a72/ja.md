```
bosonRealImag(op, η_real, η_imag, γ)
```

実部と虚部のバス相関関数が組み合わさったボソンバスを生成します

# パラメータ

  * `op::QuantumObject` : システム結合演算子で、エルミートである必要があり、フェルミオン系の場合は電荷保存と互換性があるように偶数対称でなければなりません。
  * `η_real::Vector{Ti<:Number}` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\eta_i$ の実部。
  * `η_imag::Vector{Tj<:Number}` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\eta_i$ の虚部。
  * `γ::Vector{Tk<:Number}` : バス相関関数 $\sum_i \eta_i \exp(-\gamma_i t)$ における係数 $\gamma_i$。
