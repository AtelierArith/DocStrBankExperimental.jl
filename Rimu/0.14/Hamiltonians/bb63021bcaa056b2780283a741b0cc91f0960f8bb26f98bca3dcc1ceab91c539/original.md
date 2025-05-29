```
AxialAngularMomentumHO(S; z_dim = 3, addr = BoseFS(prod(S))) <: AbstractHamiltonian
```

Angular momentum operator for application to Cartesian harmonic oscillator basis, see [`HOCartesianContactInteractions`](@ref) or [`HOCartesianEnergyConservedPerDim`](@ref). Represents the projection of angular momentum onto `z`-axis:

$$
\hat{L}_z = i \hbar \sum_{j=1}^N \left( b_x b_y^\dag - b_y b_x^\dag \right),
$$

where $b_x^\dag$ and $b_x$ are raising and lowering (ladder) operators for  a harmonic oscillator in the $x$ dimension, and simlarly for $y$.

This is implemented for an $N$ particle Fock space with creation and annihilation operators as

$$
\frac{1}{\hbar} \hat{L}_z = i \sum_{n_x=1}^{M_x} \sum_{n_y=1}^{M_y}
    \left( a_{n_x-1,n_y+1}^\dag - a_{n_x+1,n_y-1}^\dag \right) a_{n_x, n_y}.
$$

in units of $\hbar$.

Argument `S` is a tuple defining the range of Cartesian modes in each dimension and their mapping to Fock space modes in a `SingleComponentFockAddress`. If `S` indicates a 3D system the `z` dimension can be changed by setting `z_dim`; `S` should be be isotropic in the remaining `x`-`y` plane, i.e. must have `S[x_dim] == S[y_dim]`. The starting address `addr` only needs to satisfy `num_modes(addr) == prod(S)`.

# Example

Calculate the overlap of two Fock addresses interpreted as harmonic oscillator states in a 2D Cartesian basis

```jldoctest
julia> S = (2,2)
(2, 2)

julia> Lz = AxialAngularMomentumHO(S)
AxialAngularMomentumHO((2, 2); z_dim = 3, addr = BoseFS{0,4}(0, 0, 0, 0))

julia> v = DVec(BoseFS(prod(S), 2 => 1) => 1.0)
DVec{BoseFS{1, 4, BitString{4, 1, UInt8}},Float64} with 1 entry, style = IsDeterministic{Float64}()
  fs"|0 1 0 0⟩" => 1.0

julia> w = DVec(BoseFS(prod(S), 3 => 1) => 1.0)
DVec{BoseFS{1, 4, BitString{4, 1, UInt8}},Float64} with 1 entry, style = IsDeterministic{Float64}()
  fs"|0 0 1 0⟩" => 1.0

julia> dot(w, Lz, v)
0.0 + 1.0im
```
