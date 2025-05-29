```
PhaseSpacePoint
```

プロセスの位相空間における点の表現。プロセス（[`AbstractProcessDefinition`](@extref QEDbase.AbstractProcessDefinition)）、モデル（[`AbstractModelDefinition`](@extref QEDbase.AbstractModelDefinition)）、位相空間のレイアウト（[`AbstractPhaseSpaceLayout`](@extref QEDbase.AbstractPhaseSpaceLayout)）、および状態を持つ入出力粒子（[`AbstractParticleStateful`](@extref QEDbase.AbstractParticleStateful)）を含みます。

与えられたプロセスと入出力粒子の組み合わせの合法性は、構築時にチェックされます。粒子の数が不一致である場合、粒子のタイプが不一致である場合（順序が重要であることに注意）、または入射粒子が`Outgoing`方向を持つ場合、エラーがスローされます。

```julia
julia> using QEDcore

julia> using QEDbase.Mocks

julia> PhaseSpacePoint(
            MockProcess(),
            MockModel(),
            MockOutPhaseSpaceLayout(),
            (
                ParticleStateful(Incoming(), Electron(), SFourMomentum(1, 0, 0, 0)),
                ParticleStateful(Incoming(), Photon(), SFourMomentum(1, 0, 0, 0))
            ),
            (
                ParticleStateful(Outgoing(), Electron(), SFourMomentum(1, 0, 0, 0)),
                ParticleStateful(Outgoing(), Photon(), SFourMomentum(1, 0, 0, 0))
            )
        )
PhaseSpacePoint:
    process: one-photon Compton scattering
    model: perturbative QED
    phasespace layout: default
    incoming particles:
     -> incoming electron: [1.0, 0.0, 0.0, 0.0]
     -> incoming photon: [1.0, 0.0, 0.0, 0.0]
    outgoing particles:
     -> outgoing electron: [1.0, 0.0, 0.0, 0.0]
     -> outgoing photon: [1.0, 0.0, 0.0, 0.0]
```

!!! note
    `PhaseSpacePoint`sは、入出力チャネルのいずれか一方のみを設定して構築することができます。これについては、特別なコンストラクタ[`InPhaseSpacePoint`](@ref)および[`OutPhaseSpacePoint`](@ref)を参照してください。[`InPhaseSpacePoint`](@ref)および[`OutPhaseSpacePoint`](@ref)の型定義は、そのような`PhaseSpacePoint`sに対してディスパッチするために使用できます。完全な`PhaseSpacePoint`は、入出力チャネルの両方を含む場合、両方に一致します。すなわち、`psp isa InPhaseSpacePoint`および`psp isa OutPhaseSpacePoint`の両方が、pspが両方のチャネルを含む場合に真となります。完全に空の`PhaseSpacePoint`は許可されていません。

