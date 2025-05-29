```
bosonAbsorb(op, η_absorb, γ_absorb, η_emit)
```

ボソン系の吸収過程を記述するボソニックバスを生成します。相関関数は $C^{\nu=+}$ です。

# パラメータ

  * `op::QuantumObject` : 系のフェルミオンバス相互作用に従った系の生成演算子。
  * `η_absorb::Vector{Ti<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\eta_i$。
  * `γ_absorb::Vector{Tj<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\gamma_i$。
  * `η_emit::Vector{Tk<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\eta_i$。
