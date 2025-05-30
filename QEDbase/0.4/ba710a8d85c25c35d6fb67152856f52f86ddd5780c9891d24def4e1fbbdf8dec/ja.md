```
AbstractPhaseSpacePoint{PROC, MODEL, PSL, IN_PARTICLES, OUT_PARTICLES}
```

プロセスの位相空間における点の表現です。いくつかのテンプレート引数があります：

  * `PROC <:`[`AbstractProcessDefinition`](@ref)
  * `MODEL <:`[`AbstractModelDefinition`](@ref)
  * `PSL <:`[`AbstractPhaseSpaceLayout`](@ref)
  * `IN_PARTICLES <:`Tuple{Vararg{AbstractParticleStateful}}`: すべての入ってくる [`AbstractParticleStateful`](@ref) のタプル型。
  * `OUT_PARTICLES <:`Tuple{Vararg{AbstractParticleStateful}}`: すべての出てくる [`AbstractParticleStateful`](@ref) のタプル型。

次のインターフェース関数が提供されなければなりません：

  * `Base.getindex(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, n::Int)`: 指定された方向のn番目の [`AbstractParticleStateful`](@ref) を返します。無効なインデックスの場合は `BoundsError` をスローします。
  * `particles(psp::AbstractPhaseSpacePoint, dir::ParticleDirection)`: 粒子のタプル（`dir` に応じて `IN_PARTICLES` または `OUT_PARTICLES` の型）を返します。
  * [`process`](@ref): プロセスを返します。
  * [`model`](@ref): モデルを返します。
  * [`phase_space_layout`](@ref): 位相空間のレイアウトを返します。

これにより、次の関数が自動的に導出されます：

  * `momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, n::Int)`: 指定された方向のn番目の [`AbstractParticleStateful`](@ref) の運動量を返します。
  * `momenta(psp::PhaseSpacePoint, ::ParticleDirection)`: 指定された方向のすべての運動量の `Tuple` を返します。

さらに、[`AbstractPhaseSpacePoint`](@ref) の実装は、構築時にそれが有効であることを確認しなければなりません。すなわち、次の条件が満たされている必要があります：

  * `IN_PARTICLES` は `incoming_particles(::PROC)` の長さ、順序、型と一致しなければならない **または** 空の `Tuple` でなければなりません。
  * `OUT_PARTICLES` は `outgoing_particles(::PROC)` の長さ、順序、型と一致しなければならない **または** 空の `Tuple` でなければなりません。
  * `IN_PARTICLES` と `OUT_PARTICLES` の両方が空であってはなりません。

もし `IN_PARTICLES` が空でない場合、`AbstractPhaseSpacePoint <: AbstractInPhaseSpacePoint` は真です。同様に、`OUT_PARTICLES` が空でない場合、`AbstractPhaseSpacePoint <: AbstractOutPhaseSpacePoint` は真です。したがって、`IN_PARTICLES` と `OUT_PARTICLES` の両方が空でない場合、両方の `<:` 文は真です。
