```julia
    base_state(
        particle::AbstractParticleType,
        direction::ParticleDirection,
        momentum::QEDbase.AbstractFourMomentum,
        [spin_or_pol::AbstractSpinOrPolarization]
    )
```

Return the base state of a directed on-shell particle with a given four-momentum. For internal usage only.

# Input

  * `particle` – the type of the particle, i.e., an instance of an [`AbstractParticleType`](@ref), e.g. `QEDcore.Electron`, `QEDcore.Positron`, or `QEDcore.Photon`.
  * `direction` – the direction of the particle, i.e. [`Incoming`](@ref) or [`Outgoing`](@ref).
  * `momentum` – the four-momentum of the particle
  * `[spin_or_pol]` – if given, the spin or polarization of the particle, e.g. [`SpinUp`](@ref)/[`SpinDown`](@ref) or [`PolarizationX`](@ref)/[`PolarizationY`](@ref).

# Output

The output type of `base_state` depends on wether the spin or polarization of the particle passed in is specified or not.

If `spin_or_pol` is passed, the output of `base_state` is

```julia
base_state(::Fermion,     ::Incoming, mom, spin_or_pol) # -> BiSpinor
base_state(::AntiFermion, ::Incoming, mom, spin_or_pol) # -> AdjointBiSpinor
base_state(::Fermion,     ::Outgoing, mom, spin_or_pol) # -> AdjointBiSpinor
base_state(::AntiFermion, ::Outgoing, mom, spin_or_pol) # -> BiSpinor
base_state(::Photon,      ::Incoming, mom, spin_or_pol) # -> SLorentzVector{ComplexF64}
base_state(::Photon,      ::Outgoing, mom, spin_or_pol) # -> SLorentzVector{ComplexF64}
```

If `spin_or_pol` is of type [`AllPolarization`](@ref) or [`AllSpin`](@ref), the output is an `SVector` with both spin/polarization alignments:

```julia
base_state(::Fermion,     ::Incoming, mom) # -> SVector{2,BiSpinor}
base_state(::AntiFermion, ::Incoming, mom) # -> SVector{2,AdjointBiSpinor}
base_state(::Fermion,     ::Outgoing, mom) # -> SVector{2,AdjointBiSpinor}
base_state(::AntiFermion, ::Outgoing, mom) # -> SVector{2,BiSpinor}
base_state(::Photon,      ::Incoming, mom) # -> SVector{2,SLorentzVector{ComplexF64}}
base_state(::Photon,      ::Outgoing, mom) # -> SVector{2,SLorentzVector{ComplexF64}}
```

# Example

```julia
using QEDbase, QEDcore

mass = 1.0                              # set electron mass to 1.0
px,py,pz = rand(3)                      # generate random spatial components
E = sqrt(px^2 + py^2 + pz^2 + mass^2)   # compute energy, i.e. the electron is on-shell
mom = SFourMomentum(E, px, py, pz)      # initialize the four-momentum of the electron

# compute the state of an incoming electron with spin = SpinUp
# note: base_state is not exported!
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

!!! note "Iterator convenience"
    The returned objects of `base_state` can be consistently wrapped in an `SVector` for iteration using [`_as_svec`](@ref).

    This way, a loop like the following becomes possible when `spin` may be definite or indefinite.

    ```julia
    for state in QEDbase._as_svec(base_state(Electron(), Incoming(), momentum, spin))
        # ...
    end
    ```


!!! note "Conventions"
    For an incoming fermion with momentum $p$, we use the explicit formula:

    $$
    u_\sigma(p) = \frac{\gamma^\mu p_\mu + m}{\sqrt{\vert p_0\vert  + m}} \eta_\sigma,
    $$

    where the elementary base spinors are given as

    $$
    \eta_1 = (1, 0, 0, 0)^T\\
    \eta_2 = (0, 1, 0, 0)^T
    $$

    For an outgoing anti-fermion with momentum $p$, we use the explicit formula:

    $$
    v_\sigma(p) = \frac{-\gamma^\mu p_\mu + m}{\sqrt{\vert p_0\vert  + m}} \chi_\sigma,
    $$

    where the elementary base spinors are given as

    $$
    \chi_1 = (0, 0, 1, 0)^T\\
    \chi_2 = (0, 0, 0, 1)^T
    $$

    For outgoing fermions and incoming anti-fermions with momentum $p$, the base state is given as the Dirac-adjoint of the respective incoming fermion or outgoing anti-fermion state:

    $$
    \overline{u}_\sigma(p) = u_\sigma^\dagger \gamma^0\\
    \overline{v}_\sigma(p) = v_\sigma^\dagger \gamma^0
    $$

    where $v_\sigma$ is the base state of the respective outgoing anti-fermion.

    For a photon with four-momentum $k^\mu = \omega (1, \cos\phi \sin\theta, \sin\phi \sin\theta, \cos\theta)$, the two polarization vectors are given as

    $$
    \begin{align*}
    \epsilon^\mu_1 &= (0, \cos\theta \cos\phi, \cos\theta \sin\phi, -\sin\theta),\\
    \epsilon^\mu_2 &= (0, -\sin\phi, \cos\phi, 0).
    \end{align*}
    $$


!!! warning
    In the current implementation there are **no checks** built-in, which verify the passed arguments whether they describe on-shell particles, i.e. `p*p≈mass^2`. Using `base_state` with off-shell particles will cause unpredictable behavior.

