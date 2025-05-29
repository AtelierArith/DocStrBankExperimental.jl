```
hamiltonian(
        chamber::Chamber; timescale::Real=1, lamb_dicke_order::Union{Vector{Int},Int}=1,
        rwa_cutoff::Real=Inf, displacement="truncated", time_dependent_eta=false
    )
```

Constructs the Hamiltonian for `chamber` as a function of time. Return type is a function `h(t::Real, ψ)` that, itself, returns a `QuantumOptics.SparseOperator`.

**args**

  * `timescale`: e.g. a value of 1e-6 will take time to be in μs
  * `lamb_dicke_order`: Only consider terms that change the phonon number by up to this value.   If this is an `Int`, then the cutoff is applied to all modes. If this is a `Vector{Int}`,   then `lamb_dicke_order[i]` is applied to the iᵗʰ mode, according to the order in   `basis(chamber)`.   Note: this isn't quite the same thing as the Lamb-Dicke approximation since setting   `lamb_dicke_order=1` will retain, for example, terms proportional to $a^\dagger a$.
  * `rwa_cutoff`: drop terms in the Hamiltonian that oscillate faster than this cutoff.
  * `displacement`: This can be either `"truncated"`(default) or `"analytic"`.

    When an atom is irradiated, both the atom's energy and its momentum will generally be  affected. For an atom in a harmonic potential, the exchange of momentum can be modeled as  a displacement operation $D(α=iηe^{-iνt}) = exp[αa^† - α^*a]$, where $η$ is the  Lamb-Dicke parameter, which can be described equivalently as either being proportional to  the square root of the ratio of the recoil frequency with the ground state energy of the  atom's motion or as the ratio of the spread of the ground state wavefunction to the  wavelength of the laser.

    When `"truncated"` is selected, the matrix elements of $D(α)$ are computed by  constructing $α^* a, αa^†$ in a truncated basis (according to the dimension specified in  your model) and then exponentiating their difference. This has the advantage, amongst  other things, of guaranting unitarity.

    If `"analytic"` is selected, then the matrix elements are computed assuming an infinite-  dimensional Hilbert space.

    For small displacements ($η ≪ N$, where $N$ is the dimension of the motion's Hilbert  space), both of these methods will be good approximations.
  * `time_dependent_eta::Bool`: In addition to impacting the vibrational subspace directly, a  change in the trap frequency, $δν$, will also change the Lamb-Dicke parameter. Since  typically $δν≪ν$, this effect will be small $η ≈ η₀(1 + δν/2ν)$ and doesn't warrant  the additional computational resources needed to calculate and update it in time. In this  case, we can set `time_dependent_eta=false` (default), which will set $η(t) = η₀$.
