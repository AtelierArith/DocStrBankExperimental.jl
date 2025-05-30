```julia
    base_state(
        particle::AbstractParticleType,
        direction::ParticleDirection,
        momentum::QEDbase.AbstractFourMomentum,
        [spin_or_pol::AbstractSpinOrPolarization]
    )
```

与えられた四運動量を持つ指向性のオンシェル粒子の基底状態を返します。内部使用のみ。

# 入力

  * `particle` – 粒子のタイプ、すなわち、[`AbstractParticleType`](@ref) のインスタンス、例: `QEDcore.Electron`、`QEDcore.Positron`、または `QEDcore.Photon`。
  * `direction` – 粒子の方向、すなわち [`Incoming`](@ref) または [`Outgoing`](@ref)。
  * `momentum` – 粒子の四運動量
  * `[spin_or_pol]` – 指定された場合、粒子のスピンまたは偏光、例: [`SpinUp`](@ref)/[`SpinDown`](@ref) または [`PolarizationX`](@ref)/[`PolarizationY`](@ref)。

# 出力

`base_state` の出力タイプは、渡された粒子のスピンまたは偏光が指定されているかどうかによって異なります。

`spin_or_pol` が渡された場合、`base_state` の出力は次のようになります。

```julia
base_state(::Fermion,     ::Incoming, mom, spin_or_pol) # -> BiSpinor
base_state(::AntiFermion, ::Incoming, mom, spin_or_pol) # -> AdjointBiSpinor
base_state(::Fermion,     ::Outgoing, mom, spin_or_pol) # -> AdjointBiSpinor
base_state(::AntiFermion, ::Outgoing, mom, spin_or_pol) # -> BiSpinor
base_state(::Photon,      ::Incoming, mom, spin_or_pol) # -> SLorentzVector{ComplexF64}
base_state(::Photon,      ::Outgoing, mom, spin_or_pol) # -> SLorentzVector{ComplexF64}
```

`spin_or_pol` が [`AllPolarization`](@ref) または [`AllSpin`](@ref) のタイプである場合、出力は両方のスピン/偏光アライメントを持つ `SVector` になります。

```julia
base_state(::Fermion,     ::Incoming, mom) # -> SVector{2,BiSpinor}
base_state(::AntiFermion, ::Incoming, mom) # -> SVector{2,AdjointBiSpinor}
base_state(::Fermion,     ::Outgoing, mom) # -> SVector{2,AdjointBiSpinor}
base_state(::AntiFermion, ::Outgoing, mom) # -> SVector{2,BiSpinor}
base_state(::Photon,      ::Incoming, mom) # -> SVector{2,SLorentzVector{ComplexF64}}
base_state(::Photon,      ::Outgoing, mom) # -> SVector{2,SLorentzVector{ComplexF64}}
```

# 例

```julia
using QEDbase, QEDcore

mass = 1.0                              # 電子の質量を1.0に設定
px,py,pz = rand(3)                      # ランダムな空間成分を生成
E = sqrt(px^2 + py^2 + pz^2 + mass^2)   # エネルギーを計算、すなわち電子はオンシェル
mom = SFourMomentum(E, px, py, pz)      # 電子の四運動量を初期化

# スピン = SpinUp の入射電子の状態を計算
# 注意: base_state はエクスポートされていません！
electron_state = base_state(QEDcore.Electron(), Incoming(), mom, SpinUp())
```

```julia
julia> using QEDbase; using QEDcore;

julia> mass = 1.0; px,py,pz = (0.1, 0.2, 0.3); E = sqrt(px^2 + py^2 + pz^2 + mass^2); mom = SFourMomentum(E, px, py, pz)
4-element SFourMomentum with indices SOneTo(4):
 1.0677078252031311
 0.1
 0.2
 0.3

julia> electron_state = base_state(Electron(), Incoming(), mom, SpinUp())
4-element BiSpinor with indices SOneTo(4):
   1.4379526505428235 + 0.0im
                  0.0 + 0.0im
 -0.20862995724285552 + 0.0im
 -0.06954331908095185 - 0.1390866381619037im

julia> electron_states = base_state(Electron(), Incoming(), mom, AllSpin())
2-element StaticArraysCore.SVector{2, BiSpinor} with indices SOneTo(2):
 [1.4379526505428235 + 0.0im, 0.0 + 0.0im, -0.20862995724285552 + 0.0im, -0.06954331908095185 - 0.1390866381619037im]
 [0.0 + 0.0im, 1.4379526505428235 + 0.0im, -0.06954331908095185 + 0.1390866381619037im, 0.20862995724285552 + 0.0im]
```

!!! note "イテレータの便利さ"
    `base_state` の返されたオブジェクトは、[`_as_svec`](@ref) を使用してイテレーションのために一貫して `SVector` にラップできます。

    この方法で、スピンが確定しているか不確定である場合に次のようなループが可能になります。

    ```julia
    for state in QEDbase._as_svec(base_state(Electron(), Incoming(), momentum, spin))
        # ...
    end
    ```


!!! note "慣習"
    運動量 $p$ を持つ入射フェルミオンに対して、明示的な式を使用します：

    $$
    u_\sigma(p) = \frac{\gamma^\mu p_\mu + m}{\sqrt{\vert p_0\vert  + m}} \eta_\sigma,
    $$

    ここで、基本スピンorは次のように与えられます。

    $$
    \eta_1 = (1, 0, 0, 0)^T\\
    \eta_2 = (0, 1, 0, 0)^T
    $$

    運動量 $p$ を持つ出射反フェルミオンに対して、明示的な式を使用します：

    $$
    v_\sigma(p) = \frac{-\gamma^\mu p_\mu + m}{\sqrt{\vert p_0\vert  + m}} \chi_\sigma,
    $$

    ここで、基本スピンorは次のように与えられます。

    $$
    \chi_1 = (0, 0, 1, 0)^T\\
    \chi_2 = (0, 0, 0, 1)^T
    $$

    運動量 $p$ を持つ出射フェルミオンと入射反フェルミオンに対して、基底状態はそれぞれの入射フェルミオンまたは出射反フェルミオン状態のディラック随伴として与えられます：

    $$
    \overline{u}_\sigma(p) = u_\sigma^\dagger \gamma^0\\
    \overline{v}_\sigma(p) = v_\sigma^\dagger \gamma^0
    $$

    ここで、$v_\sigma$ はそれぞれの出射反フェルミオンの基底状態です。

    四運動量 $k^\mu = \omega (1, \cos\phi \sin\theta, \sin\phi \sin\theta, \cos\theta)$ を持つ光子に対して、二つの偏光ベクトルは次のように与えられます。

    $$
    \begin{align*}
    \epsilon^\mu_1 &= (0, \cos\theta \cos\phi, \cos\theta \sin\phi, -\sin\theta),\\
    \epsilon^\mu_2 &= (0, -\sin\phi, \cos\phi, 0).
    \end{align*}
    $$


!!! warning
    現在の実装では、渡された引数がオンシェル粒子を記述しているかどうかを検証する**チェックは組み込まれていません**。すなわち、`p*p≈mass^2`。オフシェル粒子で `base_state` を使用すると、予測不可能な動作を引き起こします。

