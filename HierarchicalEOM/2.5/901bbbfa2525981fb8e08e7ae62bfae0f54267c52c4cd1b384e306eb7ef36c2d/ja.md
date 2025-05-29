```
fermionAbsorb(op, η_absorb, γ_absorb, η_emit)
```

フェルミオンバスを生成し、相関関数 $C^{\nu=+}$ によるフェルミオン系の吸収プロセスを記述します。

# パラメータ

  * `op::QuantumObject` : 系とフェルミオンバスの相互作用に従った系の生成演算子。
  * `η_absorb::Vector{Ti<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\eta_i$。
  * `γ_absorb::Vector{Tj<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\gamma_i$。
  * `η_emit::Vector{Tk<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\eta_i$。
