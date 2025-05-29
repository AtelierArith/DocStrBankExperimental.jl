Particleは、輸送モンテカルロを使用してシミュレーションできるタイプを表します。次のメソッドを提供する必要があります：

```
position(el::Particle)::Position
previous(el::Particle)::Position
energy(el::Particle)::Float64
```

そのParticleタイプに格納されている現在および前の弾性散乱位置の位置。

```
T(prev::Position, curr::Position, energy::Energy) where {T <: Particle }
T(el::T, 𝜆::Float64, 𝜃::Float64, 𝜑::Float64, ΔE::Float64) where {T <: Particle }
```

2つのコンストラクタ：1つは定義されたParticleを作成するため、もう1つは別のParticleに基づいて新しいParticleを作成し、散乱角（`θ`、`ϕ`）で`λ`によって変換され、エネルギー変化`ΔE`を持ちます。

```
transport(pc::T, mat::Material)::NTuple{4, Float64} where {T <: Particle }
```

指定された`Material`内の指定された`Particle`のために（`λ`、`θ`、`ϕ`、`ΔE`）の値を生成する関数。
