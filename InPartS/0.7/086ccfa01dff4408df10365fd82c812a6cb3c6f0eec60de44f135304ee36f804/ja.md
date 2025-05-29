Simulation(PT::Type{<:AbstractParticle}; kwargs)    Simulation(ptc<:AbstractParticleContainer{N}; domainsize::NTuple{N}; kwargs...) where {N} `domainsize`のサイズを持つ`N`次元の直方体ドメインでシミュレーションを作成します。

最初の引数は、粒子タイプ`PT<:AbstractParticle{N}`であるか、粒子コンテナである必要があります。この場合、シミュレーションは`SimpleParticleContainer{N, PT}`で初期化されます。

# 引数

  * `boundaries`: ドメインの境界条件を指定します。デフォルトはすべての[`Boundary`](@ref)
  * `time`: シミュレーションクロックの初期値を設定します。デフォルトは`0.0`
  * `step`: タイムステップカウンタの初期値を設定します。デフォルトは`0x0000000000000000`
  * `registrar`: レジストラを設定します。デフォルトは[`SimpleRegistrar()`](@ref)。
  * `rng`: 擬似乱数生成器を設定します。デフォルトは[`Random.Xoshiro`](@ref)で、ランダムに選ばれたシードを使用します。
  * `threaded`: マルチスレッドの力計算を有効にします。デフォルトは`false`です。

!!! warning
    マルチスレッドの力計算は、すべての粒子コンテナでサポートされているわけではありません。

