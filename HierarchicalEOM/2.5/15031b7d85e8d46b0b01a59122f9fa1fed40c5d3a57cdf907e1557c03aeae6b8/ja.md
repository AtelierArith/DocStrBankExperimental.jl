```
fermionEmit(op, η_emit, γ_emit, η_absorb)
```

フェルミオンバスを生成し、相関関数 $C^{\nu=-}$ によるフェルミオン系の放出プロセスを記述します。

# パラメータ

  * `op::QuantumObject` : 系のフェルミオンバス相互作用に従った系の消滅演算子。
  * `η_emit::Vector{Ti<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\eta_i$。
  * `γ_emit::Vector{Ti<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\gamma_i$。
  * `η_absorb::Vector{Ti<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\eta_i$。
