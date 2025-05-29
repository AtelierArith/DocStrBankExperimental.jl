```
bosonEmit(op, η_emit, γ_emit, η_absorb)
```

ボソン系の放出過程を記述するボソンバスを生成します。相関関数 $C^{\nu=-}$ によって。

# パラメータ

  * `op::QuantumObject` : システム-ボソン-バス相互作用に従ったシステム消滅演算子。
  * `η_emit::Vector{Ti<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\eta_i$。
  * `γ_emit::Vector{Ti<:Number}` : 放出バス相関関数 $C^{\nu=-}$ の係数 $\gamma_i$。
  * `η_absorb::Vector{Ti<:Number}` : 吸収バス相関関数 $C^{\nu=+}$ の係数 $\eta_i$。
