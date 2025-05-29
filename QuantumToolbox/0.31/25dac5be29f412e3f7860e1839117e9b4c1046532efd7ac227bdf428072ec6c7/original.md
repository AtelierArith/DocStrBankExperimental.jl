```
wigner(
    state::QuantumObject{OpType},
    xvec::AbstractVector,
    yvec::AbstractVector;
    g::Real = √2,
    method::WignerSolver = WignerClenshaw(),
)
```

Generates the [Wigner quasipropability distribution](https://en.wikipedia.org/wiki/Wigner_quasiprobability_distribution) of `state` at points `xvec + 1im * yvec` in phase space. The `g` parameter is a scaling factor related to the value of $\hbar$ in the commutation relation $[x, y] = i \hbar$ via $\hbar=2/g^2$ giving the default value $\hbar=1$.

The `method` parameter can be either `WignerLaguerre()` or `WignerClenshaw()`. The former uses the Laguerre polynomial expansion of the Wigner function, while the latter uses the Clenshaw algorithm. The Laguerre expansion is faster for sparse matrices, while the Clenshaw algorithm is faster for dense matrices. The `WignerLaguerre` method has an optional `parallel` parameter which defaults to `true` and uses multithreading to speed up the calculation.

# Arguments

  * `state::QuantumObject`: The quantum state for which the Wigner function is calculated. It can be either a [`Ket`](@ref), [`Bra`](@ref), or [`Operator`](@ref).
  * `xvec::AbstractVector`: The x-coordinates of the phase space grid.
  * `yvec::AbstractVector`: The y-coordinates of the phase space grid.
  * `g::Real`: The scaling factor related to the value of $\hbar$ in the commutation relation $[x, y] = i \hbar$ via $\hbar=2/g^2$.
  * `method::WignerSolver`: The method used to calculate the Wigner function. It can be either `WignerLaguerre()` or `WignerClenshaw()`, with `WignerClenshaw()` as default. The `WignerLaguerre` method has the optional `parallel` and `tol` parameters, with default values `true` and `1e-14`, respectively.

# Returns

  * `W::Matrix`: The Wigner function of the state at the points `xvec + 1im * yvec` in phase space.

# Example

```jldoctest wigner
julia> ψ = fock(10, 0) + fock(10, 1) |> normalize

Quantum Object:   type=Ket()   dims=[10]   size=(10,)
10-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im

julia> xvec = range(-5, 5, 200)
-5.0:0.05025125628140704:5.0

julia> wig = wigner(ψ, xvec, xvec);
```

or taking advantage of the parallel computation of the `WignerLaguerre` method

```jldoctest wigner
julia> ρ = ket2dm(ψ) |> to_sparse;

julia> wig = wigner(ρ, xvec, xvec, method=WignerLaguerre(parallel=true));

```
