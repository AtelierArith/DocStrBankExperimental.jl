```
ParticleSampleable{V<:QEDlikeVariate}
```

`QEDevents.jl`の文脈におけるサンプル可能な粒子分布とサンプラーの抽象基本型です。ここで、粒子サンプル可能とは、一般的に与えられた粒子の特性（四運動量、スピン、偏光など）のランダムサンプルを生成するための何らかの`rand`関数を持つ型を指します。

粒子サンプル可能インターフェースを実装するには、以下の関数を提供する必要があります：

  * `Base.eltype(s::ParticleSampleable)`: サンプルの最も内側の型を返す
  * [`_weight(s::ParticleSampleable,x)`](@ref): 与えられたサンプル`x`の重みを返す
  * [`is_exact(s::ParticleSampleable)`](@ref): 粒子サンプル可能が正確かどうかを返す

オプションとして、以下の関数を提供することで重みの計算を強化できます：

  * [`_assert_valid_input_type(s::ParticleSampleable,x)`](@ref): 入力が正しい型であることを確認する
  * [`_assert_valid_input(s::ParticleSampleable,x)`](@ref): 入力が正しい特性を持つことを確認する
  * [`_post_processing(s::ParticleSampleable,x,res)`](@ref): `_weight`の結果に対していくつかの後処理を適用する

詳細については[`weight`](@ref)を参照してください。さらに、サンプル生成に使用されるカスタム四運動量型を提供するには、以下を実装できます：

  * [`_momentum_type(s::ParticleSampleable)`](@ref): 使用される運動量型を返す

実際のサンプリングには、以下を実装する必要があります：

  * [`_randmom(d::ParticleSampleable)`](@ref): `d`に従って運動量を返す

これらのインターフェース関数を使用して、以下のバージョンの`rand`関数が実装されます。ただし、特定のケースでは、各バージョンの`rand`関数に対してより洗練された実装がある場合（下記参照）、それを`_randmom`の代わりに実装できます。それでも、この場合は便利のために`rand`の結果を使用して`_randmom`関数も実装することをお勧めします。

!!! note "単一粒子分布"
    `SingleParticleVariate`サンプラーの場合、単一サンプルバージョンの`rand`が提供されます：

    ```julia
    Distributions.rand(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{SingleParticleVariate})
    ```

    これは、`s`から`ParticleStateful`としてランダムサンプルを返します。


!!! note "複数粒子分布"
    `MultiParticleVariate`サンプラーの場合、ミューテイティングバージョンの`rand`が実装されています：

    ```julia
    Distributions._rand!(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{MultiParticleVariate},
        out::AbstractArray{ParticleStateful})
    ```

    これは、1つまたは複数のサンプルのための`rand`の実装も提供します。


!!! note "散乱過程分布"
    `ProcessLikeVariate`分布の場合、単一サンプルバージョンの`rand`が提供されます：

    ```julia
    Distributions.rand(
        rng::Random.AbstractRNG,
        s::ParticleSampleable{ProcessLikeVariate})
    ```

    これは、各散乱過程、計算モデル、および位相空間定義を含む`PhaseSpacePoint`を返します。

